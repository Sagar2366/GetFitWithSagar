1. Shell script to install and setup jenkins on EC2 Ubuntu instance
2. Setup Kubernetes cluster
    1. Using minikube
    2. Kubeadm
    3. KOPS
    4. EKSctl
    5. AWS Portal
4. Setup cluster monitoring using Datadog
5. Setup instance EC2 Ubuntu monitoring using Datadog
6. Shell script to install and setup Python, Git and Docker
7. Dockerize any own project and deploy the same project into Kubernetes
8. Automation for ec2 management using Python and Boto3 - create, terminate, stop instances
9. Setup wavefront for Kubernetes cluster
10. Backup and recover Kubernetes cluster using Velero
11. Jenkins - Cleanup EC2 instances created by AWS BOTO3 Python script - manually, github Webhook, at particular time interval (10 PM)
12. Create Jenkins pipeline using default UI and blueocean 
13. Installation script for Sonarqube - Docker container, local setup
14. SSO + SONARQUBE integration
15. sonarqube configuration + change default port of sonarqube
16. Setup sonarqube server using
        a. Binary
        b. Docker
        c. Kubernetes
17. Sonarqube setup as server - https://docs.sonarsource.com/sonarqube/latest/setup-and-upgrade/install-the-server/
18. Setup monitoring for sonarqube - https://docs.sonarsource.com/sonarqube/latest/setup-and-upgrade/deploy-on-kubernetes/deploy-sonarqube-on-kubernetes/
19. Setup monitoring for Jenkins pipelines, freestyle jobs, nodes
20. Sonarqube alternatives - 
        a. Snyk : 
        b. DeepSource : https://deepsource.com/sonarqube-alternatives
        c. Vercode
21. Backup and recover jenkins 

Terraform Assignments
22. Document Alternatives of the Terraform and their differences
23. CI/CD pipeline for Terraform automation - [Soon to be updated]
24. Manage Kubernetes cluster using Terraform
    a. EKS
    b. Kubeadm
    c. AKS
25. Comparison between Terraform community version and Terraform Cloud
26. Shell script to setup Terraform on any machine - Ubuntu, Windows, Mac
27. Manage Kubernetes secrets using Hashicorp Vault - https://developer.hashicorp.com/vault/docs/platform/k8s
28. Document on Hashicorp tools
29. Dockerise your application using Terraform
30. Jenkins CI/CD pipeline for your application - Build, test, and deploy (Docker image creation and container creation)
31. Create EC2 instance into private subnet using Terraform
32. Create vpc, subnet, network interfaces to be used and create EC2 instances
33. Create public IP address and EC2 instance with public address created using terraform and print ec2 instance ID and public IP
34. Create 2 LoadBalancer using terraform and output the results
35. Update one of the above LoadBalancer resource using Terraform 
36. Delete/Destroy only the second loadbalancer using terraform
37. Store terraform state in multiple backends - remote, local and s3
38. Document type of Loadbalancer and their differences
39. Use input variables to enter S3 bucket name and create S3 bucket, store file into s3 bucket using Terraform
40. Create, backup and recover EKS cluster using terraform and Velero
41. Jenkins CI/CD pipeline to deploy -
    a. EC2
    b. S3
    c. EKS
    d. VPC and subnets
    Nidhish - ✅, Siddharth - ✅
42. Jenkins CI/CD pipeline to upgrade EKS cluster
43. Terraform to manage Hashicorp vault
44. EBS CSI Add on :
    a. Create EKS cluster without installing EBS CSI addon -> Deploy any application in K8S cluster which requires pv and pvc 
    Note : You will get an error to bound and create PV, PVC
    b. To fix above error, add EBS CSI plugin to create PV in AWS and try setting up application again in K8S cluster.
45. Create your own Terraform module for EC2 instance and EKS and publish it to Terraform registry
46. Terraform plan to manager AWS Users, Groups and IAM policies
47. Terraform plan to create AKS and GKE cluster

## Observability 
1. Blog on Grafana and it's other prodcuts
2. 
3.
4.
5.


Upcoming
1. EC2 instance and Cluster migration


References -
https://github.com/terraform-aws-modules/terraform-aws-eks/blob/v19.16.0/examples/complete/main.tf
https://github.com/hashicorp/learn-terraform-provision-eks-cluster/blob/main/main.tf
https://developer.hashicorp.com/vault/tutorials/kubernetes/kubernetes-sidecar
https://developer.hashicorp.com/vault/tutorials/kubernetes/vault-secrets-operator
https://docs.aws.amazon.com/eks/latest/userguide/ebs-sample-app.html


