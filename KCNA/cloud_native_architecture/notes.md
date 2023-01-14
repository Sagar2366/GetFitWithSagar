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