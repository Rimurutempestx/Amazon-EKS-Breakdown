# Overview

In the past few weeks I have seen a overwhelming amount of people explaing their struggles with Amazon EKS, I have decided to create this repository to do my best to breakdown some of the more mandatory skill aspects of EKS. Amazon EKS is by no means a easy service to use that you can just learn over night, having heavily been involved with EKS for the last few years of my life. I dived straigt into EKS when I was only 15. I have experienced more struggles and obstacles than I can even remember. That being said I want to do my best to help the community in anyway I can considering that were all apart of this together after all.

## Section 1: EKS Breakdown

## Section 2: EKS Roadmap

# Section 1 EKS Breakdown:

# Complexity

Amazon EKS is a complex system, and users need to have a good understanding of Kubernetes and its associated concepts to use it effectively. I will be breaking down all of the main concepts that I feel are the most important being Helm, Pods, Kube ctl, Kube-proxy, Kubernetes API, Control plane, Worker nodes, Kubernets objects, Kubernetes controllers, Kubernetes namespace, Kubernetes labels, Kubernetes networking, Kubernetes storage, Kubernetes security. We will do a deep dive into all of them later but for now we are just going to give a summary of each component.

![image](https://user-images.githubusercontent.com/106786020/226471115-309f7eea-244e-485c-b9b6-7f7d22df76b1.png)

Helm: "Helm  is the package manager for Kubernetes. Helm is the best way to find, share, and use software built for Kubernetes. Helm and Kubernetes work like a client/server application. The Helm client pushes resources to the Kubernetes cluster via kubernetes API." you can either use pre-built helm charts or take time to create your own for more specific needs.

![image](https://user-images.githubusercontent.com/106786020/226474614-fbd62249-1177-4797-9cb8-39b8ff331092.png)

Pods: A pod is the smallest deployable unit in the Kubernetes system. A pod represents a single instance of a running process in a cluster, and it encapsulates one or more containers that share the same network namespace and storage volumes. Pods are the basic building blocks of a Kubernetes application, and they provide a convenient way to package, deploy, and manage containerized applications. Pods can be created and managed using the Kubernetes API, and they can be automatically scheduled and scaled by the Kubernetes control plane.

![image](https://user-images.githubusercontent.com/106786020/226475011-d81ef633-012a-4cd1-9db3-5358332651d6.jpeg)

Kube ctl: Kubectl is a command-line tool used for managing Kubernetes clusters, including those running on Amazon Elastic Kubernetes Service (EKS). It is the primary interface for interacting with Kubernetes clusters and allows developers and administrators to deploy, inspect, and manage containerized applications running on a Kubernetes cluster. Think of it like a remote controller for your Kubernetes clusters.

![image](https://user-images.githubusercontent.com/106786020/226475694-4ddbc5e1-503e-4831-b7f4-a4ebb809eb53.png)

Kube-proxy: Kube-proxy is a network proxy and load balancer that runs on each worker node in a Kubernetes cluster. It is responsible for managing network traffic between Kubernetes services and their associated pods. Kube-proxy uses the Kubernetes API to monitor the state of the cluster, including the creation and deletion of pods and services. It then updates the IP tables on the worker nodes to ensure that traffic is correctly routed to the appropriate pods and services. I find this to be one of the more helpful tools as it pertains to Kubernetes, also one of the tools I use the most.

![image](https://user-images.githubusercontent.com/106786020/226476632-d0c7cf03-8901-4308-8b0d-51fd01f611a2.png)

Kubernetes API: The Kubernetes API is a RESTful API that exposes the functionality of a Kubernetes cluster. It is the primary interface for interacting with a Kubernetes cluster and is used by developers and administrators to manage and deploy containerized applications.
The Kubernetes API provides a declarative model for specifying the desired state of a Kubernetes cluster and allows users to manipulate the state of the cluster by creating, updating, and deleting Kubernetes objects such as pods, services, deployments, and replica sets.

Control plane: The control plane is the set of components that manage the Kubernetes cluster. These components include the Kubernetes API server, etcd (a distributed key-value store for storing cluster state), the Kubernetes controller manager, and the Kubernetes scheduler.

Worker nodes: Worker nodes are instances that run your containerized applications and services. These nodes are responsible for running the Kubernetes pod and container tasks that make up your application. When you create an Amazon EKS cluster, you define the desired number of worker nodes, their instance type, and the Amazon Machine Image (AMI) to use for provisioning.

Kubernetes Objects: Kubernetes objects are the fundamental building blocks used to define, configure, and manage applications and services deployed on the Kubernetes cluster. Exmaplas include: Pods, Deployments, Services, ConfigMaps, Secrets, and Statefulsets.

Kubernetes controllers: Kubernetes controllers are components that are responsible for managing the state of Kubernetes objects, ensuring that the desired state is maintained and automatically correcting any deviations from that state. There are many diffrent types of Kubernetes controllers, so you will have to identify your needs before making any rash decisions.

Kubernetes namespace: Kubernetes namespace is a way to create a virtual cluster inside a Kubernetes cluster. A namespace provides a way to logically partition resources and create a virtual cluster, which helps to manage and organize resources within the cluster.

Kubernetes labels: Kubernetes labels are key-value pairs that are used to organize and categorize resources within a Kubernetes cluster. Labels are metadata that can be attached to Kubernetes objects such as pods, services, and deployments, allowing you to easily select and manage related resources.

Kubernets networking: Kubernetes networking refers to the set of mechanisms used to enable communication between the various components of a Kubernetes cluster. Kubernetes networking allows pods to communicate with each other and with other services in the cluster, and enables load balancing and traffic management for those services. Kubernetes networking in Amazon EKS is built on top of the Kubernetes networking model.

Kubernetes storage: Kubernetes storage refers to the mechanisms used to provide persistent storage to containerized applications running in a Kubernetes cluster. Kubernetes storage allows for the persistent storage of data even if a pod or container is restarted, rescheduled, or terminated.

Kubernetes security: Kubernetes security refers to the set of mechanisms used to secure the various components of a Kubernetes cluster, including the control plane, worker nodes, and applications running in the cluster.

# Setup

Setting up Amazon EKS can be a difficult and time-consuming process, requiring expertise in infrastructure and networking. Setting up a effective EKS environment involves everal steps, including configuring the cluster, setting up networking and security, and deploying applications there are multiple steps to ensure proper setip of your EKS environment.

Planning the architecture: Before setting up the cluster, it's important to plan the overall architecture of your application, including the number of nodes, the types of workloads, and the required networking and storage configurations. This way you can ensure that everything works cohesively and it makes it alot easier to take the proper steps in launching your EKS deployment.

![image](https://user-images.githubusercontent.com/106786020/227004761-7128762b-17db-4286-a366-2d4c96a89dfb.png)

Creating the cluster/clusters: You can create an Amazon EKS cluster using the AWS Management Console, AWS CLI, or AWS CloudFormation. It's important to configure the cluster with the appropriate settings, including the Kubernetes version, networking, and security policies. Everything does not have to be flawless on this end at first, but it acts as a good base to have a cluster to build around.

Setup Networking: Amazon EKS supports a variety of networking solutions, including the Amazon VPC CNI, Calico, and Weave Net. It's important to choose a networking solution that meets your requirements and configure it appropriately. Typically you should have no trouble finding what suit your needs, I usually just refer to the AWS documentation.

<img width="947" alt="image" src="https://user-images.githubusercontent.com/106786020/227005218-1b76858b-1225-48bd-8e04-d75a9e4e0ec7.png">

Configure security: Kubernetes security in Amazon EKS involves securing the control plane, worker nodes, and applications running in the cluster. This can involve configuring RBAC, network policies, container security features, logging and monitoring, and compliance and governance frameworks. There will be a separate section for security later on for a deeper dive into it.

Deploy applications: Once the cluster is set up, you can deploy applications using Kubernetes manifests or Helm charts. It's important to configure the appropriate resources, such as pods, services, and persistent volumes, and to test the application thoroughly to ensure it meets your requirements.

Monitor and optimize: It's important to monitor the performance of your Amazon EKS environment and optimize it as needed to ensure optimal resource utilization and cost-effectiveness. This can involve using tools like AWS CloudWatch and Kubernetes Dashboard to track resource usage and identify opportunities for optimization. In a way this category can also fall under the same page as secuity, but it's still important to monitor your application at all times do to things like compute or storage failures or even the fact that AWS could update there services and you can find a better way to optimize performance.

# Cost

The cost of using Amazon EKS (Elastic Kubernetes Service) can vary based on a number of factors, such as the size of the cluster, the number of nodes, the storage and networking requirements, and the region where the cluster is deployed.

There are two main components to the cost of using EKS: the cost of the EKS control plane and the cost of the worker nodes. The control plane manages the Kubernetes master nodes and is charged at an hourly rate based on the region. The worker nodes are EC2 instances that run your application workloads and are charged based on the instance type, the number of nodes, and the usage time.

In addition to these costs, you may also incur charges for other services that you use in conjunction with EKS, such as Elastic Load Balancers, Elastic Block Storage volumes, and other AWS services.

# Scalability

The scalability on EKS typically comes down to the way you want to scale and how fast and cost effectively you want to do it. I've worked closely with five different types that I use on a weekly basis.

Horizontal Pod Autoscaling: EKS supports Kubernetes' Horizontal Pod Autoscaler (HPA), which automatically scales the number of pods in a deployment based on CPU utilization or other metrics. By setting up an HPA, you can ensure that your application can handle varying levels of traffic.

Cluster Autoscaling: EKS also supports Cluster Autoscaler, which automatically adjusts the number of worker nodes in the cluster based on the demand for resources. This is particularly useful when you have unpredictable traffic patterns, and you don't want to overprovision your cluster.

Manual Scaling: You can also manually scale your cluster by adding or removing worker nodes. This can be done through the EKS console, AWS CLI, or SDKs. Manual scaling is useful when you want more fine-grained control over your cluster's capacity.

Spot Instances: EKS also supports using Spot instances, which are spare EC2 instances that are available at a lower cost than On-Demand instances. You can use Spot instances to scale your cluster and save costs, but you need to be prepared for the possibility of instances being terminated with short notice.

Node Groups: Node Groups are a way to group worker nodes with similar characteristics, such as instance type or storage configuration. By using Node Groups, you can have more control over the scaling of specific subsets of your cluster.


# Security

Securing your Amazon EKS environment is essential for protecting sensitive data, ensuring business continuity, meeting compliance requirements, and mitigating cyber threats. By implementing a comprehensive security strategy, you can help ensure the safety and reliability of your EKS environment. Here are some of the best practices that I use for securing my environments.

Secure the EKS Control Plane: The EKS control plane manages the Kubernetes master nodes, and it's critical to secure it to prevent unauthorized access. You can secure the control plane by using AWS Identity and Access Management (IAM) to manage access to EKS resources and by enabling encryption for communication between the control plane and worker nodes.

Secure Worker Nodes: You should secure your worker nodes by ensuring that only authorized users and services can access them. You can use IAM roles to grant access to worker nodes, and you can also use AWS security groups and network ACLs to restrict inbound and outbound traffic to your worker nodes.

Secure Kubernetes API Server: The Kubernetes API server exposes an HTTP API that enables users to interact with the cluster. You should secure the API server by using Transport Layer Security (TLS) encryption and by restricting access to authorized users.

Use Network Security Best Practices: You should implement network security best practices such as using a Virtual Private Cloud (VPC) to isolate your EKS cluster from the public internet, using AWS security groups to control inbound and outbound traffic, and using VPC flow logs to monitor network traffic.

Implement Security Policies: You should implement security policies such as limiting the use of privileged containers, using pod security policies to enforce security requirements for pods, and enabling auditing to monitor activity within the cluster.

Use AWS Security Services: AWS provides a number of security services that can help you secure your EKS cluster, such as AWS Security Hub, AWS CloudTrail, and AWS Config. You should use these services to monitor your cluster for security events, detect and respond to security threats, and maintain compliance with security standards.

# Networking

Networking can be a complicated part of Amazon EKS, and users need to have a good understanding of Kubernetes networking concepts to configure it correctly. It is always best to break the concepts down separately.

![image](https://user-images.githubusercontent.com/106786020/227033080-d24d06df-a8ce-4fc5-9c48-ea52b81c4877.png)

To start off with the concepts I am sure whoever is reading this is already familiar with the bascic types of networking. Things like VPC's, Subnets, Scurity groups, and Load balancing shouldn't have to be explained, so I will just stick with the core 3 networking type that pertain to EKS.

Kube-proxy: kube-proxy is a Kubernetes networking component that runs on each worker node in the cluster. Its primary function is to provide a network proxy and load balancer for Kubernetes services running on the worker nodes.

kube-proxy works by setting up a set of network rules on the worker node's operating system to forward incoming traffic to the appropriate pod in the cluster. It also manages the virtual IP address (VIP) assigned to the service, which allows clients to connect to the service without needing to know the IP addresses of the individual pods.

kube-proxy operates in three different modes:

1. User space mode: In this mode, kube-proxy runs as a userspace daemon on the worker node, and it uses iptables rules to forward traffic to the appropriate pod. This mode is less performant than other modes, but it can be used in environments where the kernel does not support the other modes.

2. IPVS mode: In this mode, kube-proxy uses the Linux kernel's IPVS (IP Virtual Server) module to perform load balancing and service proxying. This mode is highly performant and scalable and is the recommended mode for EKS clusters running on Linux worker nodes.

3. IPTables mode: In this mode, kube-proxy uses iptables rules to forward traffic to the appropriate pod. This mode is similar to user space mode, but it uses a more efficient implementation of iptables.

Kube-dns service: kube-dns is a Kubernetes add-on service that provides name resolution for Kubernetes services using DNS. It is responsible for mapping Kubernetes service names to their corresponding IP addresses, which enables clients to connect to services using their names rather than their IP addresses.

kube-dns is composed of two components: a DNS server and a DNS agent. The DNS server is responsible for serving DNS requests for the Kubernetes cluster, while the DNS agent runs as a pod on each worker node in the cluster and watches for changes to the Kubernetes service and pod configurations.

When a Kubernetes service is created, kube-dns creates a DNS record for the service name in the cluster's DNS namespace. This record maps the service name to a cluster IP address assigned to the service. When a client sends a DNS query for the service name, the DNS server returns the IP address of one of the pods associated with the service. This enables clients to connect to the service without needing to know the IP addresses of individual pods.

kube-dns is an essential component of the Kubernetes networking stack in EKS and plays a critical role in ensuring that services are accessible and discoverable within the cluster.

Container networking: Container networking refers to the networking model used by Kubernetes to facilitate communication between containers running on different worker nodes within the cluster. Container networking is a crucial aspect of EKS since it enables Kubernetes to schedule and manage containers in a highly distributed and scalable manner. Container networking in EKS is implemented using a Container Network Interface (CNI) plugin. A CNI plugin is responsible for configuring the networking environment for containers running on a worker node. The CNI plugin creates network namespaces and virtual network interfaces for containers and sets up rules in the kernel's networking stack to enable communication between them.

# Monitoring

 Monitoring and logging are essential parts of operating any Kubernetes cluster, and this can be challenging in Amazon EKS. EKS provides several monitoring capabilities to help you observe the health of your Kubernetes cluster and applications running on it. 
 
 Metrics: EKS provides a set of pre-configured metrics that you can use to monitor your cluster, such as CPU and memory utilization, network traffic, and disk usage. These metrics can be viewed using Amazon CloudWatch.
 
Logging: EKS supports logging of Kubernetes API server events, container logs, and node logs. These logs can be viewed using various tools, such as Amazon CloudWatch Logs and Elasticsearch.

Tracing: EKS integrates with AWS X-Ray to enable tracing of requests through applications running on the cluster. This can help you identify performance issues and troubleshoot errors.

Kubernetes Dashboard: EKS includes a Kubernetes Dashboard that provides a graphical user interface for monitoring and managing your cluster. The dashboard displays real-time information about your cluster, such as resource utilization and the status of Kubernetes objects.

Prometheus: EKS supports Prometheus, a popular open-source monitoring system for Kubernetes. With Prometheus, you can collect custom metrics and perform more advanced monitoring and analysis.

![image](https://user-images.githubusercontent.com/106786020/227364323-682d0932-f4b7-48d3-83f6-7236c405700c.png)

# Maintenance 

 Maintenance can be a time-consuming process, and users need to keep their cluster up-to-date with the latest patches and upgrades. 
 Maintenance in Amazon EKS involves several key concepts, including: 
 
 Cluster upgrades: Amazon EKS automatically manages the upgrade process for the Kubernetes control plane and worker nodes, ensuring that the cluster stays up-to-date with the latest security patches and features.
 
Node maintenance: Amazon EKS provides tools to manage node maintenance, including the ability to drain nodes before performing maintenance tasks, such as patching or updating node software.

Scaling: Amazon EKS makes it easy to scale worker nodes up or down based on demand, using the AWS Auto Scaling feature.
Monitoring: Amazon EKS provides built-in monitoring capabilities, including integration with AWS CloudWatch and the ability to view cluster and node-level metrics.

Logging: Amazon EKS provides built-in logging capabilities, including integration with AWS CloudTrail and the ability to view logs for Kubernetes components, applications, and containers.

High availability: Amazon EKS is designed to be highly available, with automatic failover for the Kubernetes control plane and worker nodes.

Security: Amazon EKS provides several security features, including network isolation, encryption in transit and at rest, and integration with AWS Identity and Access Management (IAM) for authentication and authorization.

# Integration 

Integrating Amazon EKS with other services can be complicated, and users need to have a good understanding of the integration process. There are some that you should definitely focus on more than others though like:

Kubernetes API server: Amazon EKS integrates with the Kubernetes API server, providing a managed control plane for Kubernetes clusters. This allows users to manage their clusters using standard Kubernetes tools and APIs.

AWS Identity and Access Management (IAM): Amazon EKS integrates with IAM to provide authentication and authorization for Kubernetes API calls. This allows users to control access to their Kubernetes clusters using IAM policies.

AWS VPC networking: Amazon EKS integrates with Amazon VPC networking, allowing users to control network traffic to and from their Kubernetes clusters. This provides secure and isolated network access to Kubernetes applications.

AWS Load Balancers: Amazon EKS integrates with AWS Load Balancers, allowing users to easily expose their Kubernetes applications to the internet. This provides scalability and availability for Kubernetes applications.

AWS CloudFormation: Amazon EKS integrates with AWS CloudFormation, allowing users to create and manage their Kubernetes clusters using CloudFormation templates. This provides a way to automate the creation and management of Kubernetes clusters.

AWS CloudTrail: Amazon EKS integrates with AWS CloudTrail, allowing users to log and monitor all API activity for their Kubernetes clusters. This provides visibility into user activity and helps with compliance and auditing.

# Support

Although Amazon provides support for EKS, getting help can be challenging, and users need to have a good understanding of the platform to troubleshoot issues effectively.

Node Groups: A node group is a set of Amazon EC2 instances that are used to run Kubernetes nodes. Node groups can be created and managed separately from the rest of the Kubernetes control plane, making it easier to scale your cluster as needed.

Control Plane: The control plane is the set of Kubernetes components that manage the state of your cluster. Amazon EKS provides a managed control plane that automatically scales to meet the needs of your workload.

Worker Nodes: Worker nodes are the Amazon EC2 instances that run your Kubernetes pods. These nodes are managed by the control plane and can be added or removed as needed to meet the demands of your workload.

Cluster: The Kubernetes cluster is the set of nodes and control plane components that work together to manage your workload. Amazon EKS provides a managed Kubernetes control plane, but you are responsible for managing your worker nodes.

Managed Node Groups: Managed node groups provide a simpler way to manage your worker nodes. You can create a managed node group with a few clicks in the AWS Management Console or using the AWS CLI or SDKs, and Amazon EKS takes care of the rest, including automatically updating the AMI and managing the lifecycle of the instances.

Fargate: Amazon EKS also supports running Kubernetes pods on AWS Fargate, a serverless compute engine for containers. With Fargate, you don't need to manage any infrastructure, and you only pay for the resources your pods consume.

# Section 2 EKS Roadmap:

![EKS Road Map PDF.pdf](https://github.com/Rimurutempestx/Amazon-EKS-Breakdown/files/11094172/EKS.Road.Map.PDF.pdf)

In this section I will be explaining the best ways to learn Amazon EKS and the ways to incorporate each service with your Amazon EKS environment.

### Deployment: 

![image](https://user-images.githubusercontent.com/106786020/228369548-1e1b03fc-5f1a-47b9-8b03-799b4249b5ef.png)

Deployment in my opinon is the core aspect of Amazon EKS, it's like the cake itself. You need to have a cake in order to add frosting, sprinkles, and what not. So you always want to start with testing or visualizing a deployment first so its always great to have knowledge of deployment services first. The ones I would start with would be Kubernetes manifest, Container images, Kubernetes CLI, EKS console, CI/CD tools.

Kubernetes manifest: Kubernetes manifest is a YAML file that describes the desired state of the resources in a Kubernetes cluster. It can include specifications for a variety of resources such as deployments, services, pods, config maps, and more. Its a great way to setup your resources in EKS. The Kubernetes manifest defines the desired configuration of the Kubernetes objects and their relationships to each other. It is used by Kubernetes to create and manage the resources in the cluster. The manifest also enables developers to define complex deployment scenarios, including scaling and updating applications. 

you can create a Kubernetes manifest file locally on your computer and use the kubectl command-line tool to apply it to your cluster. You can also use tools like AWS CloudFormation or AWS CDK to manage your Kubernetes resources using manifests.

Container images: 

container images are self-contained, executable packages that include everything needed to run a piece of software, including the code, runtime, system tools, libraries, and settings. Container images are typically built using a Dockerfile, which specifies the dependencies and configuration needed to create the image. Once an image is built, it can be stored in a container registry, such as Amazon Elastic Container Registry (ECR), where it can be easily accessed and distributed to other users or teams. container images are used to deploy applications and services to the cluster. A container image can be specified in a Kubernetes manifest, and Kubernetes will use that image to create containers that run the application. When a container is created from an image, it runs in an isolated environment with its own file system, network, and resources, providing a consistent and reproducible environment for the application.

Container images can also be used to implement a continuous delivery (CD) pipeline, allowing developers to quickly and easily build, test, and deploy code changes to a Kubernetes cluster.

Kubernetes CLI: The kubectl command-line tool, which is a standard command-line interface for interacting with Kubernetes clusters. kubectl is used to deploy and manage applications and resources on a Kubernetes cluster running in Amazon EKS. With kubectl, you can perform a variety of tasks such as:

- Creating, modifying, and deleting Kubernetes resources such as pods, services, and deployments. 
- Scaling and updating applications running on the Kubernetes cluster.
- Viewing and troubleshooting logs and events.
- Managing Kubernetes configuration and secrets.

To use kubectl with Amazon EKS, you need to first configure the tool with credentials to access your cluster. This can be done by running the aws eks update-kubeconfig command, which downloads the necessary authentication information and configures kubectl to use it. Once kubectl is configured, you can use it to interact with your Amazon EKS cluster as you would any other Kubernetes cluster.

EKS console: The EKS Console in Amazon EKS is a web-based graphical user interface (GUI) for managing Kubernetes clusters running on the Amazon EKS service. It provides an intuitive interface for viewing and managing the resources in your cluster, including nodes, pods, services, and deployments. The EKS Console includes a dashboard that provides an overview of the state of your cluster, as well as details about the nodes and resources running in the cluster. It also provides a visual editor for creating and managing Kubernetes resources such as pods and services.

While the EKS Console can be a useful tool for managing Kubernetes clusters, it is not a replacement for the kubectl CLI or other command-line tools. Some tasks may be easier to perform using the EKS Console, while others may be more efficient using the command-line tools. The EKS Console is intended to provide an additional option for managing your cluster, alongside the existing command-line tools and APIs.

CI/CD tools: There are many Continuous Integration/Continuous Deployment (CI/CD) tools that can be used with Amazon EKS to help automate the build, test, and deployment of applications and services to Kubernetes clusters. Some popular CI/CD tools that work well with EKS include:

- AWS CodePipeline: A fully managed continuous delivery service that helps you automate your release pipelines for fast and reliable application and infrastructure updates.
- Jenkins: An open-source automation server that can be used to build, test, and deploy applications to Kubernetes clusters using plugins and integrations with other tools.
- GitLab CI/CD: An integrated CI/CD solution that provides automated testing, building, and deploying of applications using GitLab's pipeline feature.
- CircleCI: A cloud-based CI/CD platform that allows you to build, test, and deploy applications using a simple configuration file.
Spinnaker: An open-source multi-cloud continuous delivery platform that can be used to deploy applications to Kubernetes clusters.

These CI/CD tools can be used to create and manage pipelines that automatically build, test, and deploy containerized applications to Kubernetes clusters running on Amazon EKS. By automating the deployment process, teams can accelerate the delivery of new features and updates while ensuring consistency and reliability across different environments.






















