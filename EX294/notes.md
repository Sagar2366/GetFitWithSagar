
Read the instruction carefully.
1. There will be one controller machine and 5 nodes.
2. You will be provided the root login and root password, and you have to create playbooks via admin user. [ Login on controller node with root then switch to admin user ]

3. Create all your playbooks in /home/admin/ansible [ mkdir /home/admin/ansible ]

4. Create config and inventory file in /home/admin/ansible/5. Create a roles directory in /home/admin/ansible/ [ mkdir /home/admin/ansible/roles]



Note: 
vim command will not be working, so you have to install vim in your controllermachine (yum install vim -y) but vi command will be accessible.

First step -> read instructions carefully 

Second step -> ssh <given user>@< master/controller node name 
                                                   
Third key step -> yum install vim -y (Optional Part just to configure vim in controllernode)
  
In admin home directory to create the .vimrc file
  vim /home/admin/.vimrc
  set ai
  set ts=2
  set et
  set cursorcolumn
  
  
Step1: Read the instructions carefully, there you’ll get ip addresses and fqdn of all nodes& root password of controller node. 
       And folder name where you have to put all playbooks and config file. 
       Also username of managed node and some other things.
       Remember:- We won’t need root password anywhere. 
                  User name of managed node and controller node would be same.
  
Step2: ssh tocontrollernode on root account. 
       Then switch user( su -username).
  
Step3: Install and setup vim, install ansible

Step4: Create folder with that name given in instruction
  
Step5: Start solving questions
