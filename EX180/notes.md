## Red Hat EX180 Practice Questions

## Introduction
The Red Hat Certified Specialist in Containers and Kubernetes exam (EX180) tests your skills and knowledge of the fundamentals of containers and OpenShift, including the ability to find, customize, run, and manage containerized services in both standalone environments and environments with both Kubernetes and OpenShift. Now that you've gone through all the objectives, it is time to test your newfound knowledge on the practice exam to prepare for the real exam! In this lab, you will be asked to perform a series of tasks similar to what you will be asked to do in the actual exam. Good luck, and please use this practice exam as many times as you need before taking the exam.

## Task 1.
```
Edit the registries:
sudo vi /etc/containers/registries.conf
Enter your cloud_user password.
Find the the registries.search parameter line and add 'registry-1:5000' to end of registry (remember to press i to enter insert mode).
Find the registries.insecure parameter line and add 'registry-1:5000' as an insecure registry.
Save and quit the file by pressing Escape followed by :wq.
```

## Task 2.
```
Pull the latest Nginx image docker.io/library/nginx:
podman pull docker.io/library/nginx
Verify the pull was complete:
podman images
Clear your screen:
clear
Run a container using the Nginx image with the specified parameters:
podman run -d --name=web-vol -v /home/cloud_user/web:/usr/share/nginx/html/:Z --pod task-2 docker.io/library/nginx
Verify you can access the web page:
curl localhost:8081
Save a copy of the container logs to a file named web-vol.log:
podman logs web-vol > web-vol.log
Verify the copy of the container logs was saved:
ls web-vol.log
Review the contents of web-vol.log copy:
less web-vol.log
```

## Task 3.
```
Pull the latest MySQL image from docker.io/library/mysql (this may take a few minutes):
podman pull docker.io/library/mysql
clear your screen.
Verify the image was pulled:
podman images
Start a container with the specified variables:
podman run -d --name=mysql-llama -e MYSQL_PASSWORD=badpass -e MYSQL_USER=guru -e MYSQL_ROOT_PASSWORD=supersecret -e MYSQL_DATABASE=llama -p 3306:3306 docker.io/library/mysql
clear your screen.
Verfiy the MySQL instance is running and confirm that the llama database is present:
echo "show databases;" | mysql -uguru -pbadpass --protocol tcp -h localhost
Make a directory named mysql_logs:
mkdir mysql_logs
Copy the log file /var/lib/mysql/mysql/general_log_213.sdi to the directory:
podman cp mysql-llama:/var/lib/mysql/mysql/general_log_213.sdi mysql_logs/
Verify the log file was copied successfully:
ls -l mysql_logs/
```

## Task 4.
```
Log in to the registry:
podman login -u cloud_user registry-1:5000
Enter your cloud_user password.
View the images:
podman search registry-1:5000/
Inspect the image for alternate tags:
skopeo inspect docker://registry-1:5000/nginx | less
clear your screen.
Start the container using the image with the alternate tag (not latest):
podman run -d --name=web-default -p 8080:80 registry-1:5000/nginx:useme
Verify the default message:
curl localhost:8080
clear your screen.
Connect to the container:
podman exec -it web-default bash
Edit the file:
vi /usr/share/nginx/html/index.html
Clear Replace Me and type A guru was here!.
Save and quit the file by pressing Escape followed by :wq.
Exit the file:
exit
Verify the change using curl:
curl localhost:8080
Commit the new container to new image:
podman commit web-default registry-1:5000/nginx:web-guru
clear your screen.
Review the images to confirm registry-1:5000/nginx with the tag web-guru was created successfully:
podman images
Build and Run Custom Images
```

## Task 5.
```
View the images:
podman images
Push your new image to registry-1:5000:
podman push registry-1:5000/nginx:web-guru registry-1:5000/nginx:web-guru
clear your screen.
Stop the existing container:
podman stop web-default
Start a new one container:
podman run -d --name=web-guru -p 8080:80 registry-1:5000/nginx:web-guru
Verify the change was saved in the new image and is present in the new container (You should see the A guru was here! message):
curl localhost:8080
Save the image to a tar file:
podman save -o guru-web.tar registry-1:5000/nginx:web-guru
List guru-web.tar:
ls guru-web.tar
```

## Task 6.
```
List the docker directory:
ls docker
List the files:
ls files
Move into the docker directory:
cd docker
Copy the ZIP and tar files to the docker directory:
cp ../files/* .
List the files:
ls
clear your screen.
Edit the Dockerfile (you can review the file in this Git repo):
vim Dockerfile
Change the color of the comments to grey for better readability:
:hi Comment ctermfg=grey
Under #Please use image registry.access.redhat.com/ubi8/ubi:8.4, enter:
FROM registry.access.redhat.com/ubi8/ubi:8.4
Under Set yourself as the Maintainer of this image, enter:
MAINTAINER <YOUR_NAME>
Under #Provide a brief description of the image next to LABEL description=, enter (make sure you are using straight quotation marks):
"New web server"
Under #Install nginx and unzip, enter:
RUN yum install -y nginx unzip
Under #Use ENV to set the variable PORT to 90, enter:
ENV PORT=90
Under #Use the variable $PORT to expose the set port, enter:
EXPOSE $PORT
Under #Copy nginx_conf.zip to /tmp/, enter:
COPY nginx_conf.zip /tmp/
Under #Extract /tmp/nginx_conf.zip to /etc/nginx and overwrite any existing files, enter:
RUN unzip -o /tmp/nginx_conf.zip -d /etc/nginx/
Under #Extract llama_cart.tar to /usr/share/nginx/html/, enter:
ADD llama_cart.tar /usr/share/nginx/html/
Under #Set the workdir to /tar_file/ and copy llama_cart.tar to this directory without uncompressing it, enter:
WORKDIR /tar_file/
COPY llama_cart.tar .
Under #Set the container to start "nginx" with options "-g" and "daemon off" as overwritable options (hint: use ENTRYPOINT and CMD), enter:
ENTRYPOINT ["nginx"]
CMD ["-g", "daemon off;"]
Save and quit the file by pressing Escape followed by :wq.
```

## Task 7.
```
Build the image (this may take a few minutes):
podman build -t llama-cart:v1 .
clear your screen:
Review the images:
podman images
Start a new container:
podman run -d --name=llama-web -p 8090:90 localhost/llama-cart:v1
clear your screen.
Confirm the container is running:
curl localhost:8090
clear your screen.
Navigate to the cloud_user home directory:
cd
Navigate to server_info.txt:
cat server_info.txt
Copy the public DNS name, paste it into a new browser, and add :8090 to the end to confirm the custom image is running.
Creating Applications with OpenShift
```

## Task 8: CodeReady Containers
```
Create new project named guru-php with display name of Test hello guru project:
oc new-project guru-php --display-name="Test hello guru project"
clear your screen.
Create the new PHP app with the specified configuration and this GitHub repo:
oc new-app --name=hello-guru --as-deployment-config php~https://github.com/linuxacademy/Red-Hat-Certified-Specialist-in-Containers-and-Kubernetes --context-dir=php-hello-world -l app=hello-guru
clear your screen.
Retrieve the resources and wait until the pod build is ready (this may take a few minutes):
oc get all | less
Retrieve the service:
oc get service
Expose the service:
oc expose service hello-guru
Retrieve the routes:
oc get routes
Test the route:
curl <ROUTE_HOSTNAME>
```

## Task 9: OpenShift Sandbox
```
Once you're logged in to the OpenShift sandbox, make sure you're using the existing <username>-dev project.
Click the shell icon (>_) in the top-right.
Once the shell loads, click on the Open terminal in a new tab icon.
Create the new PHP app with the specified configuration and this GitHub repo (this may take a few minutes):
oc new-app --name=hello-guru --as-deployment-config php~https://github.com/linuxacademy/Red-Hat-Certified-Specialist-in-Containers-and-Kubernetes --context-dir=php-hello-world -l app=hello-guru
clear your screen.
Check the resources and wait until the pod build is ready (this may take a few minutes):
oc get all
Check the resources:
oc get all
Confirm the hello-guru pod is running.
clear your screen.
Expose the hello-guru service:
oc expose service hello-guru
Retrieve the routes:
oc get routes
Test the route:
curl <ROUTE_HOSTNAME>
```

## Task 10: CodeReady Containers
```
Create new project named inventory:
oc new-project inventory
clear your screen.
Download the template file:
curl https://raw.githubusercontent.com/linuxacademy/Red-Hat-Certified-Specialist-in-Containers-and-Kubernetes/main/multi-container/multi_test.yaml -o multi_test.yaml
Verify the file was created:
ls multi_test.yaml
clear your screen.
Publish the template to the current project:
oc create -f multi_test.yaml
Verify the template was created:
oc get templates
clear your screen.
Process the template, save it to a file named processed_template.yaml, and set the following parameters:
oc process -f multi_test.yaml -p NAME=fruit-stand -p DATABASE_NAME=fruit_stand -p DATABASE_USER=guru -p DATABASE_PASSWORD=badpass -p DATABASE_ADMIN_PASSWORD=badidea -l app=guru-fruit > processed_template.yaml
Verify the file was created:
ls processed_template.yaml
clear your screen.
Create the application:
oc create -f processed_template.yaml
clear your screen.
Retrieve the resources (it may take a few minutes until the build is complete):
oc get all | less
Retrieve the resources with the above command to confirm pod/fruit-stand and pod/postgresql are running.
Scroll down to the route section, copy the route hostname, and paste it into a new browser.
Switch to the CodeReady Containers web UI interface and, under Topology, click on the Open URL icon.
```

## Task 11: OpenShift Sandbox
```
Switch to the <username>-stage project:
oc project <username>-stage
Download the template file:
curl https://raw.githubusercontent.com/linuxacademy/Red-Hat-Certified-Specialist-in-Containers-and-Kubernetes/main/multi-container/multi_test.yaml -o multi_test.yaml
Verify the file was created:
ls multi_test.yaml
clear your screen.
Publish the template to the current project:
oc create -f multi_test.yaml
Verify the template has been created:
oc get templates
clear your screen.
Process the template and save to a file named processed_template.yaml:
oc process -f multi_test.yaml -p NAME=fruit-stand -p DATABASE_NAME=fruit_stand -p DATABASE_USER=guru -p DATABASE_PASSWORD=badpass -p DATABASE_ADMIN_PASSWORD=badidea -l app=guru-fruit > processed_template.yaml
Verify the file exists:
ls processed_template.yaml
clear your screen.
Create the application:
oc create -f processed_template.yaml
clear your screen.
Retrieve your resources (it may take a few minutes until the build is complete):
oc get all | less
Retrieve the resources to confirm pod/fruit-stand and pod/postgresql are running:
oc get all
clear your screen.
Retrieve the routes:
oc get routes
Navigate back to the Topology, move into the <username>-stage project, and click on the Open URL icon.
```

## Task 12: CodeReady Containers
```
Confirm you're logged in to the inventory project:
oc project
Build the required directories:
mkdir -p logs/pod-fruit-stand logs/pod-postgres
List the logs:
ls -ls logs
clear your screen.
Retrieve the pods:
oc get pods
Sync /var/log from the running fruit-stand pod to the respective directory. Note: It will show an rsync error in CRC if rsync is not installed. The command will still work by falling back to tar:
oc rsync <FRUIT_STAND_POD>:/var/log/ logs/pod-fruit-stand/
clear your screen.
Retrieve the pods:
oc get pods
Sync /var/log from the running postgresql pod to the respective directory. Note: It will show an rsync error in CRC if rsync is not installed. The command will still work by falling back to tar:
oc rsync <POSTGRESQL_POD>:/var/log/ logs/pod-postgres/
clear the screen.
Check the directories:
ls logs/*
```

## Task 13: OpenShift Sandbox
```
Confirm you're in the <username>-stage project:
oc project
Build the required directories:
mkdir -p logs/pod-fruit-stand logs/pod-postgres
List the logs:
ls logs
Retrieve the pods:
oc get pods
Sync /var/log from the running fruit-stand pod to the respective directory. Note: It will show an rsync error in OpenShift sandbox if rsync is not installed. The command will still work by falling back to tar:
oc rsync <FRUIT_STAND_POD>:/var/log/ logs/pod-fruit-stand/
Retrieve the logs:
ls logs/pod-fruit-stand/
clear your screen.
Retrieve the pods:
oc get pods
Sync /var/log from the running postgresql pod to the respective directory:
oc rsync <POSTGRESQL_POD>:/var/log/ logs/pod-postgres/
Retrieve the logs:
ls logs/pod-postgres/
```

