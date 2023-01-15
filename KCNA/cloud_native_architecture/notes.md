## Cloud NAtive Architecture Fundamentals
Characteristics of Cloud Native Architecture -
1. Automation
2. Self healing
3. Scalable
4. Cost efficient
5. Esy to maintain
6. Secure by default

The autoscaling pattern describes the dynamic adjustment of resources based on the current demand
Horizontal - Spawning new compute resources - application process, virtual machines
Vertical - change in size of the underlying hardware

Serverless - Function As A service, you can just provide the application code, while the cloud provider chooses the right environment to run your application. CloudEvent (provides a specification of how event data should be structured)

Open Standards :
The image-spec defines how to build and package container images. While the runtime-spec specifies the configuration, execution environment and lifecycle of containers. A more recent addition to the OCI project is the Distribution-Spec, which provides a standard for the distribution of content in general and container images in particular.

* OCI Spec: image, runtime and distribution specification on how to run, build an distribute containers
* Container Network Interface (CNI): A specification on how to implement networking for Containers.
* Container Runtime Interface (CRI): A specification on how to implement container runtimes in container orchestration systems.
* Container Storage Interface (CSI):A specification on how to implement storage in container orchestration systems.
* Service Mesh Interface (SMI): Ap specification on how to implement Service Meshes in container orchestration systems with a focus on Kubernetes.

Cloud Native roles and SRE :
Cloud Architect : Responsible for adoption of cloud technologies, designing application landscape and infrastructure, with a focus on security, scalability and deployment mechanisms.
DevOps Engineer : Often described as a simple combination of developer and administrator, but that doesn't do the role justice. DevOps engineers use tools and processes that balance out software development and operations. Starting with approaches to writing, building, and testing software throughout the deployment lifecycle.
Security Engineer : Perhaps the easiest role to grasp. Nonetheless, the role of security engineers has changed significantly. Cloud technologies have created new attack vectors and these days the role has to be lived much more inclusive and as an integral part of a team
DevSecOps Engineer : In an effort to make security an integral part of modern IT environments, the DevSecOps Engineer combines the roles of the previous two. This role is often used to build bridges between more traditional development and security teams.
Data Engineer : Data engineers face the challenge of collecting, storing, and analyzing the vast amounts of data that are being or can be collected in large systems. This can include provisioning and managing specialized infrastructure, as well as working with that data.
Full-Stack Developer : An all-rounder who is at home in frontend and backend development, as well as infrastructure essentials.


Site Reliability Engineer (SRE)
A role with a stronger definition is the Site Reliability Engineer (SRE). SRE was founded around 2003 at Google and became an important job for many organizations. The overarching goal of SRE is to create and maintain software that is reliable and scalable. To achieve this, software engineering approaches are used to solve operational problems and automate operation tasks.
To measure performance and reliability, SREs use three main metrics:
* Service Level Objectives (SLO): “Specify a target level for the reliability of your service.” - A goal that is set, for example reaching a service latency of less that 100ms.
* Service Level Indicators (SLI): “A carefully defined quantitative measure of some aspect of the level of service that is provided” - For example how long a request actually needs to be answered.
* Service Level Agreements (SLA): “An explicit or implicit contract with your users that includes consequences of meeting (or missing) the SLOs they contain. The consequences are most easily recognized when they are financial – a rebate or a penalty – but they can take other forms.” - Answers the question what happens if SLOs are not met.
Around these metrics, SREs might define an error budget. An error budget defines the amount (or time) of errors your application can have, before actions are taken, like stopping deployments to production.


ReplicaSet
A controller object that ensures a desired number of pods is running at any given time. ReplicaSets can be used to scale out applications and improve their availability. They do this by starting multiple copies of a pod definition.

Deployment
The most feature-rich object in Kubernetes. A Deployment can be used to describe the complete application lifecycle, they do this by managing multiple ReplicaSets that get updated when the application is changed by providing a new container image, for example. Deployments are perfect to run stateless applications in Kubernetes.

StatefulSet
Considered a bad practice for a long time, StatefulSets can be used to run stateful applications like databases on Kubernetes. Stateful applications have special requirements that don't fit the ephemeral nature of pods and containers. In contrast to Deployments, StatefulSets try to retain IP addresses of pods and give them a stable name, persistent storage and more graceful handling of scaling and updates.

DaemonSet
Ensures that a copy of a Pod runs on all (or some) nodes of your cluster. DaemonSets are perfect to run infrastructure-related workload, for example monitoring or logging tools.

Job
Creates one or more Pods that execute a task and terminate afterwards. Job objects are perfect to run one-shot scripts like database migrations or administrative tasks.

CronJob
CronJobs add a time-based configuration to jobs. This allows running Jobs periodically, for example doing a backup job every night at 4am.

Ingress provides a means to expose HTTP and HTTPS routes from outside of the cluster for a service within the cluster. It does this by configuring routing rules that a user can set and implement with an ingress controller.

NetworkPolicies are a simple IP firewall (OSI Layer 3 or 4) that can control traffic based on rules. You can define rules for incoming (ingress) and outgoing traffic (egress). A typical use case for NetworkPolicies would be restricting the traffic between two different namespaces.

* PersistentVolumes (PV)An abstract description for a slice of storage. The object configuration holds information like type of volume, volume size, access mode and unique identifiers and information how to mount it.
* PersistentVolumeClaims (PVC)A request for storage by a user. If the cluster has multiple persistent volumes, the user can create a PVC which will reserve a persistent volume according to the user's needs.

Horizontal Pod Autoscaler (HPA)
Horizontal Pod Autoscaler (HPA) is the most used autoscaler in Kubernetes. The HPA can watch Deployments or ReplicaSets and increase the number of Replicas if a certain threshold is reached. Imaging your Pod can use 500MiB of memory and you configured a threshold of 80%. If the usage is over 400MiB (80%), a second Pod will get scheduled. Now you have a capacity of 1000MiB. If 800MiB is used, a third Pod will get scheduled and so on.

Cluster Autoscaler
Of course, there is no point in starting more and more Replicas of Pods, if the Cluster capacity is fixed. The Cluster Autoscaler can add new worker nodes to the cluster if the demand increases. The Cluster Autoscaler works great in tandem with the Horizontal Autoscaler.

Vertical Pod Autoscaler
The Vertical Pod Autoscaler is relatively new and allows Pods to increase the resource requests and limits dynamically. As we discussed earlier, vertical scaling is limited by the node capacity.
