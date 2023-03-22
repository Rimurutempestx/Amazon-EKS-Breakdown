# Overview

In the past few weeks I have seen a overwhelming amount of people explaing their struggles with Amazon EKS, I have decided to create this repository to do my best to breakdown some of the more difficult aspects of EKS. Amazon EKS is by no means a easy service to use that you can just learn over night, having heavily been involved with EKS for the last few years of my life. I dived straigt into EKS when I was only 15. I have experienced more struggles and obstacles than I can even remember. That being said I want to do my best to help the community in anyway I can considering that were all apart of this together after all.

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



























