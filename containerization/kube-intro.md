# Kubernetes Overview

### Introduction

Kubernetes stands out as the leading container orchestration tool. We've successfully deployed numerous containers so far, all managed within a single Docker engine. However, the potential risk arises when this singular Docker engine encounters a failure. In the unfortunate event of a Docker engine failure, all containers hosted within that engine will inevitably go offline, rendering them inaccessible to users.

Anticipating this concern, you might be contemplating implementing high availability by deploying multiple Docker engines. And you're absolutely correct; for production environments, it's crucial to establish a cluster of Docker engines.

This involves not just a singular Docker node but multiple Docker nodes. Additionally, a **master node** is indispensable in orchestrating and overseeing the activities of these Docker nodes, ensuring coordinated and efficient management of the containerized workloads. This clustering approach enhances the reliability and resilience of the overall system, mitigating the impact of potential failures on the availability of applications.

The **master node** takes charge of instructing the Docker nodes on which containers to run. Its primary responsibility is to efficiently distribute containers across the Docker nodes, stepping in seamlessly if any of the Docker nodes encounters a failure.

You have the flexibility to manually run containers on the active Docker engines. Alternatively, you can enable containers to start automatically on the Docker engine, streamlining the deployment process.

In the scenario where containers on the other nodes fail due to a node failure, the system exhibits resilience. The containers undergo migration to a healthy node, ensuring uninterrupted operation despite the setback. This process, whereby containers dynamically adapt to node failures and relocate to maintain availability, is aptly termed **container orchestration.**

You will operate with a **master node,** commonly referred to as the orchestrator, overseeing the orchestration process. Complementing the orchestrator are clusters of Docker nodes, or worker nodes, where the orchestrator efficiently allocates and manages containers.

Pooling all your Docker nodes into a unified resource cluster enhances fault tolerance, creating a resilient environment. While container orchestration is typically associated with production environments, it's worth noting that you can also run regular containers within this orchestrated infrastructure. The orchestration framework provides a robust foundation for managing containerized workloads, ensuring reliability and efficient resource utilization.

In today's dynamic landscape, building your own orchestration platform is a feasible endeavor. However, with various established orchestration tools available in the market, you can leverage existing solutions to streamline the process.

#### Noteworthy orchestration tools include:
- **Docker Swarm** A direct offering from Docker.
- **Kubernetes** stands out as the most renowned orchestration tool.
- **Mesosphere Marathon** From Apache
- 
  #### While cloud-based solutions include:
- **AWS ECS (Elastic Container Service) and AWS EKS (Elastic Kubernetes Service)** AWS offerings
- **Azure Container Service** From Azure
- **Google Container Engine** Google Cloud offering
- **OpenShift**
- **CoreOS Fleet**

This diverse range of orchestration tools caters to different needs, whether on-premises or cloud-based, allowing you to choose the one that aligns best with your requirements. You also have the option of developing an in-house orchestration platform to meet specific needs.

Among the various orchestration tools available, Kubernetes stands out as the most widely recognized. Notably, technologies like EKS are essentially implementations of Kubernetes. Additionally, on Mesosphere Marathon, you have the capability to run a Kubernetes cluster.

Kubernetes is particularly prevalent across numerous environments, and the question arises: why is it so widely adopted? The answer harks back to a significant announcement from Google in 2014. At that time, Google revealed that every aspect of Google Gmail, and indeed everything in their infrastructure, was powered by Linux containers. This infrastructure launch included an astonishing rate of over 2 billion containers deployed every week. This revelation undoubtedly contributed to the widespread adoption of Kubernetes, solidifying its reputation as a leading orchestration tool in the industry. What made it astonishing was not just the concept of containers but the staggering scale **involved—2 billion containers.** 

The key insight lies in understanding the disposable nature of containers. Their disposability allows for seamless updates; any modifications needed can be effortlessly implemented by replacing containers. Visualizing this on a global scale, considering Google's data centers spread across the world, underscores the immense task of managing **billions of containers,** revealing the transformative power of containerization in large-scale operations. That's a significant revelation that sparked widespread interest as everyone sought to understand the intricacies of this remarkable achievement. It's important to note that Kubernetes originated from Google's internal infrastructure management tool called **Borg,** designed to handle Linux container LXC orchestration. The initial version of Kubernetes, however, did not exist during the inception of **Borg.**

**In mid-2014,** Google made a pivotal move by introducing Kubernetes as an open-source project, essentially sharing an evolved version of **Borg** with the wider community. This marked the formal beginning of Kubernetes' journey as a collaborative and open platform.

The milestone continued to evolve, and by **mid-2015,** the stable version of Kubernetes, version 1.0, was released. This release represented a significant step forward in the maturity and stability of Kubernetes, making it accessible to a broader audience for container orchestration.

Furthermore, Google established a partnership with the **Cloud Native Computing Foundation (CNCF),** leading to the project's management falling under the purview of CNCF. This partnership solidified the commitment to fostering open-source collaboration and innovation within the Kubernetes ecosystem. The **CNCF,** in addition to managing the project, offers certifications and training programs for Kubernetes. This initiative serves to standardize knowledge and proficiency in Kubernetes across the industry.

The **year 2016** marked a turning point for Kubernetes as it transitioned into the mainstream. During this period, auxiliary tools such as **kubeadm,** **Kops** and **Minikube** began emerging. These tools played a crucial role in simplifying the process of creating and configuring Kubernetes clusters, contributing to the broader adoption and accessibility of Kubernetes in various deployment scenarios.

In **late 2016,** a pivotal case study emerged from Pokémon Go, instilling greater confidence in utilizing Kubernetes for production environments. This real-world example showcased the platform's robustness and reliability.

Moving into **2017,** significant strides in enterprise adoption of Kubernetes were witnessed. **Google** made a substantial contribution to this landscape, and **IBM** announced the Istio controller for ingress controls, resembling an application load balancer in functionality. **GitHub** made a noteworthy transition to running on Kubernetes, underlining the platform's suitability for large-scale and critical applications. In a symbolic move, **Oracle** joined the **Cloud Native Computing Foundation (CNCF),** aligning with the broader Kubernetes community.

Reflecting on these milestones, it might seem as though these events transpired in a distant past, but it's essential to acknowledge that we're referring to the year 2017—a relatively recent timeframe in the fast-evolving world of container orchestration and cloud-native technologies.

Despite its relatively short existence, Kubernetes has rapidly matured into a robust platform, and its integration into Google's operations underscores its reliability. Google, a pioneer in the tech industry, has been leveraging Kubernetes for decades, attesting to its enduring utility and effectiveness.

Beyond the formidable Google infrastructure, Kubernetes offers a plethora of remarkable features. It's important to clarify that Kubernetes isn't a direct replacement for the Docker engine; instead, it excels at managing clusters of Docker engines. Moreover, Kubernetes is versatile enough to extend its capabilities beyond Docker and can seamlessly manage clusters of other container runtime environments, such as Rocket. This flexibility and inclusivity contribute to the broad appeal and adoption of Kubernetes across diverse containerized environments.

### Kubernetes boasts an array of impressive features.

- **Service discovery and load balancing:** Seamlessly integrated into Kubernetes. When you create a container, referred to as a "pod" in this context, it is automatically discovered by the load balancer, and any updates to the load balancer are handled seamlessly. This dynamic interaction ensures efficient service discovery and load distribution within the cluster.

- **Storage orchestration:** Kubernetes provides seamless integration with a variety of storage solutions, including Storage Area Network(SAN), Network-Attached Storage(NAS), and even cloud-based solutions like EBS volumes and Ceph storage. The extensive list of supported storage options contributes to a robust and flexible storage orchestration environment within Kubernetes. As a result of these capabilities, confidence in running stateful containers has grown substantially. 

- **Automated rollouts and rollbacks:** Kubernetes makes it effortlessly simple to deploy a new image version and equally easy to roll back in case the update proves problematic. This process, akin to what we do in AWS Elastic Beanstalk, but at a faster pace, ensuring a swift and efficient deployment lifecycle.

- **Automatic bin packing:** It intelligently places your containers on the most suitable node, ensuring optimal resource utilization based on the specified requirements. This meticulous allocation of resources contributes to the efficient utilization of computing resources.

- **Self-healing:** If a node becomes unavailable. It promptly resurrects your containers on a live node, ensuring continuous operation in the event of a node failure. Additionally, containers are actively monitored, allowing for proactive management similar to the Auto Scaling group in other environments. In the event of an instance failure, the Auto Scaling group launches a replacement, showcasing the self-healing capability, which operates even faster than traditional Auto Scaling groups.

- **Secret and configuration management:** Kubernetes provides robust configuration management capabilities, allowing you to handle configurations in the form of variables, volumes, and encoded secrets. These encoded secrets add an extra layer of security to sensitive information.

- **Batch Execution:** Kubernetes can manage not only services but also your batch and CI workloads. It has the capability to replace failing containers if desired.

- **Horizontal Scaling**: Easily scale your application up and down using a simple command, a UI, or automatically based on CPU usage.

- **IPv4/IPv6 Dual-Stack:** Kubernetes supports the allocation of both IPv4 and IPv6 addresses to Pods and Services.

- **Designed for Extensibility:** Extend the features of your Kubernetes cluster without the need to modify upstream source code.

While there are many more features to explore, these are some of the standout functionalities of Kubernetes. For a more comprehensive understanding, you can refer to the [Kubernetes documentation](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/) which provides a detailed overview of the platform's capabilities. 

### Architecture of Kubernetes
Involves several services working together to form the complete cluster.

![]()

At its core, Kubernetes comprises two main components:

- **Master Node:** Manages worker nodes, where Docker engines run.
- **Worker Node:** Hosts Docker engines and executes containers.
Notably, you don't interact directly with the worker nodes to run containers; instead, you communicate your instructions to the master node.

Access to the master node doesn't involve direct logins. Instead, you connect to it using a client, providing information about the containers you wish to run. The master node, also referred to as the **control plane**, takes actions based on these instructions.

#### Within the master node or control plane, four essential services are at play:

1. **API Server:** Acts as a communication hub, processing requests and managing the cluster state.

2. **Scheduler:** Determines which worker node should run a new pod based on resource requirements and constraints.
  
3. **Controller Manager:** Ensures that the desired state of the cluster matches the actual state, handling node failures and replication.
  
4. **etcd:** A distributed key-value store that stores the configuration data of the cluster.

Beyond these fundamental services, additional services and add-ons can be incorporated into the master node.

#### On the worker node, three critical services operate:

1. **kubelet:** Ensures that containers are running in a Pod.

2. **kube-proxy:** Maintains network rules on nodes, facilitating communication between pods and external network traffic.

3. **Docker Engine:** Executes and manages containers on the worker node.

In upcoming sections, we'll delve into each of these services to gain a comprehensive understanding of the Kubernetes architecture.


# Understanding Kubernetes Control Plane Components

## Control Plane Overview

In the realm of Kubernetes, the control plane, anchored by the master node, is a pivotal aspect that facilitates communication and coordination within the cluster. Let's delve into the key components of the control plane.

### 1. Kube API Server

The **Kube API Server** serves as the linchpin of the control plane, acting as the main orchestrator. It handles all incoming and outgoing communication, enabling seamless interactions within the Kubernetes cluster. When instructions are sent to Kubernetes, the Kube API Server receives and processes them, passing the information to other crucial services like the scheduler, etcd, and worker nodes. It exposes the Kubernetes API, allowing for the integration of third-party tools such as monitoring agents, logging agents, and web dashboards. The Kube API Server serves as the front end for the entire Kubernetes cluster, offering a point of interaction for administrators and DevOps personnel. The `kubectl` command-line interface is commonly used to connect to the API server, providing a versatile tool for managing the cluster. Additionally, a web dashboard is available for a graphical interface, complementing the range of available integrations.

### 2. etcd

The second component on the master node is **etcd**, a key-value store designed for storing the critical information of the Kubernetes cluster. The Kube API Server interacts with etcd, storing and retrieving cluster information. Etcd contains runtime details, and it is crucial to regularly back up this data. In the event of a failure, losing etcd data results in the loss of current cluster state information. Etcd essentially stores the real-time state of everything within the cluster, making it a fundamental element for Kubernetes operations.

These two components, the Kube API Server and etcd, form the backbone of the control plane, orchestrating the communication, coordination, and storage essential for the effective functioning of a Kubernetes cluster.

### 3. Scheduler

The **Scheduler**, our third component, plays a vital role in the master node. It is responsible for intelligently scheduling containers onto the appropriate worker nodes. When a scheduling request is received, the Scheduler meticulously chooses the right worker node based on various factors such as resource requirements, hardware and software specifications, and any specified policies. Factors like affinity and anti-affinity rules, specifying preferences or restrictions on node selection, are considered. The Scheduler automates this decision-making process, but you can also provide explicit policies to guide its choices.

### 4. Controller Manager

The **Controller Manager**, our fourth component, is a collective term for multiple controllers, simplifying the nomenclature. It encapsulates various controllers responsible for specific tasks:

- **Node Controller:** Monitors the health of worker nodes, taking corrective actions if any node goes down.
- **Replication Controller:** Monitors pods (think of them as containers for now) and ensures the specified number of replicas are maintained.
- **Endpoint Controller:** Populates the endpoint object, a crucial component we'll delve into later.
- **Service Controller:** Manages service objects, defining a set of pods and a policy to access them.
- **Token Controller:** Handles authentication and authorization within the cluster.

These components collectively form the Controller Manager, addressing different aspects of cluster management. While each serves a distinct purpose, together they contribute to the overall health, resilience, and functionality of the Kubernetes cluster.

# Worker Node Components in Kubernetes

Now, let's explore the essential components on the worker nodes in a Kubernetes cluster.

## 1. Kubelet

The first component on the worker node is the **Kubelet**—an agent that runs on every node. It listens to commands and requests from the Kubernetes master. When the Scheduler determines that a specific worker node should run a container, it assigns this responsibility to the Kubelet. The Kubelet then fetches the container image and executes the container, handling the heavy lifting involved, much like the commands you run with `docker run -p -v ...`.

## 2. Kube Proxy

**Kube Proxy** is a network proxy running on every node in the cluster. It facilitates network communication and allows you to set network rules, akin to security group rules. You can specify rules to allow or deny certain traffic, providing control over network access within the cluster.

## 3. Container Runtime Environment

The most critical component on the worker node is the **Container Runtime Environment**. Kubernetes is highly flexible in this regard—you can have Docker, Containerd, Rocket, or Kubernetes CRI as your runtime environment. Unlike Docker Swarm, which restricts you to using only Docker Engine, Kubernetes allows the use of various runtime environments.

## Add-ons

In addition to these components, you can include optional add-ons based on your requirements. These add-ons may include DNS services, a web UI, resource monitoring tools, or cluster-level logging. Third-party vendors often specialize in providing these components, offering enhanced capabilities for logging, monitoring, user interfaces, and more.

## Recap of the Architecture

To recap the architecture:

- The Kubernetes master comprises the API server, scheduler, controller manager, etcd.
- The kubelet on the worker node acts as an agent, executing instructions from the master.
- kube-proxy facilitates network communication and rule-setting.
- The container runtime environment allows flexibility in choosing runtime technologies.

Remember not to confuse `kubectl` (our tool for connecting) with `kubelet` (the agent running on the worker node). While `kubectl` is used for connecting and managing, `kubelet` performs the heavy lifting for container execution.

# Understanding kube-proxy and Pod in Kubernetes

## Kube Proxy: The Network Proxy

**kube-proxy** serves as a network proxy in Kubernetes. When you need to expose a Pod to the external world, you can utilize kube-proxy. It allows you to set network rules, providing a flexible approach to handling Pod communication.

## Docker Engine and Pod

The **Docker Engine** is where your containers run, encapsulated within a Pod. Now, let's dive into understanding what exactly a Pod is.

### Pod and Container Relationship

A **Pod** in Kubernetes is akin to a Virtual Machine (VM) in its relationship with the process running inside it. Consider a VM running a Tomcat process—it allocates resources such as network, RAM, CPU, and storage to the process. Similarly, a Pod allocates all necessary resources to a container running inside it. The container, resembling a process, utilizes these resources. Think of the Pod as the VM providing isolation and resource allocation for the container.

### Importance of Pod in Kubernetes

Why does Kubernetes use Pods instead of directly running containers? The key lies in abstraction. Kubernetes supports various container runtime environments like Docker, Rocket, and CRI. The Pod acts as an abstraction layer, providing a consistent interface regardless of the underlying container runtime environment. Without the Pod abstraction, this level of flexibility and compatibility across runtimes would be challenging to achieve.

# Understanding Pods in Kubernetes

## Overview of Pods

Now, let's delve into the concept of Pods in Kubernetes.

### Abstraction with Pod

A **Pod** in Kubernetes is a standardized set of commands and configurations, providing an abstraction layer regardless of the underlying technology. It allows us to provide instructions to the Pod, which, in turn, manages the execution for the container running inside it. If, for instance, you have a Tomcat process running in a Pod, Tomcat becomes the container running on a specific port (e.g., 8080), and the Pod assigns an IP address for access.

### Pod and Container Relationship

In a Pod, you can have one or multiple containers. The Pod allocates resources to the containers. Consider the examples:
- Pod One: A Pod with one container inside.
- Pod Two: A Pod with a container and an attached volume.
- Pod Three: A Pod with two containers and a shared volume between them.

### Running Multiple Containers in a Pod

While you can have multiple containers in a Pod, it's typically recommended to have one main container and additional helper containers. The main container performs the primary task, while helper containers assist with activities like logging or monitoring. For example, a Pod with Tomcat might have a sidecar container assisting with log streaming.

### Interactions and Overlay Network

Pods can be distributed across multiple worker nodes, and they interact using an **overlay network**. This network acts as a virtual private network (VPC) connecting all nodes, with each node having its subnet. The bridge zero within each node functions as a switch, enabling communication between Pods on the same node. When Pods on different nodes need to interact, the overlay network forwards the request through a routing mechanism, facilitating communication across nodes.

In summary, Pods provide a standardized and abstracted environment for containerized applications, with the overlay network enabling seamless communication within and across nodes in a Kubernetes cluster.


# Setting Up a Kubernetes Cluster

Enough theory about the architecture, let's get practical and set up a Kubernetes Cluster. There are multiple ways to achieve this:

## Manual Setup (Not Recommended for Production)

The hardest way involves manually setting up a Kubernetes Cluster. However, this approach is not recommended for production environments and is best suited for learning purposes.

## Tools for Easier Setup

### MiniKube
- Ideal for testing and learning.
- Sets up a single-node Kubernetes Cluster on your computer, usually within a virtual machine using VirtualBox.
- Useful for understanding Kubernetes components but not recommended for production.

### Kubeadm
- Popular for setting up production-ready, multi-node Kubernetes clusters.
- Allows you to define the number of worker nodes, making it scalable.
- Requires running specific commands on the master node and worker nodes to establish the connection.

### Kops (Kubernetes Operations)
- Considered the most stable option for production.
- Originally designed for AWS but now supports Google Cloud, Digital Ocean, and OpenStack.
- Provides a reliable way to set up and manage your Kubernetes Cluster with fewer manual steps.

In our guide, we'll explore both MiniKube and Kops to cater to testing, learning, and production requirements.


