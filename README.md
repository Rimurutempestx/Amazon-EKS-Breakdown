### Overview

In the past few weeks I have seen a overwhelming amount of people explaing their struggles with Amazon EKS, I have decided to create this repository to do my best to breakdown some of the more difficult aspects of EKS. Amazon EKS is by no means a easy service to use that you can just learn over night, having heavily been involved with EKS for the last few years of my life. I dived straigt into EKS when I was only 15. I have experienced more struggles and obstacles than I can even remember. That being said I want to do my best to help the community in anyway I can considering that were all apart of this together after all.

## Complexity

Amazon EKS is a complex system, and users need to have a good understanding of Kubernetes and its associated concepts to use it effectively. I will be breaking down all of the main concepts that I feel are the most important being Helm, Pods, Kube ctl, Kube-proxy, Kubernetes API, Control plane, Worker nodes, Kubernets objects, Kubernetes controllers, Kubernetes namespace, Kubernetes labels, Kubernetes networking, Kubernetes storage, Kubernetes security. We will do a deep dive into all of them later but for now we are just going to give a summary of each component.

![image](https://user-images.githubusercontent.com/106786020/226471115-309f7eea-244e-485c-b9b6-7f7d22df76b1.png)

Helm: "Helm  is the package manager for Kubernetes. Helm is the best way to find, share, and use software built for Kubernetes. Helm and Kubernetes work like a client/server application. The Helm client pushes resources to the Kubernetes cluster via kubernetes API." you can either use pre-built helm charts or take time to create your own for more specific needs.

![image](https://user-images.githubusercontent.com/106786020/226474614-fbd62249-1177-4797-9cb8-39b8ff331092.png)

Pods: A pod is the smallest deployable unit in the Kubernetes system. A pod represents a single instance of a running process in a cluster, and it encapsulates one or more containers that share the same network namespace and storage volumes. Pods are the basic building blocks of a Kubernetes application, and they provide a convenient way to package, deploy, and manage containerized applications. Pods can be created and managed using the Kubernetes API, and they can be automatically scheduled and scaled by the Kubernetes control plane.

![image](https://user-images.githubusercontent.com/106786020/226475011-d81ef633-012a-4cd1-9db3-5358332651d6.jpeg)

Kube ctl: Kubectl is a command-line tool used for managing Kubernetes clusters, including those running on Amazon Elastic Kubernetes Service (EKS). It is the primary interface for interacting with Kubernetes clusters and allows developers and administrators to deploy, inspect, and manage containerized applications running on a Kubernetes cluster. Think of it like a remote controller for your Kubernetes clusters.

![image](https://user-images.githubusercontent.com/106786020/226475694-4ddbc5e1-503e-4831-b7f4-a4ebb809eb53.png)












