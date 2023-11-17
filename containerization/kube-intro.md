# Kubernetes 
Kubernetes is the most popular container orchestration

tool and we'll understand what it is

and why it is so famous.

So we have run so many containers us so far, and

all the containers were running in one single docker engine.

But what if that docker engine fails?

Obviously all the containers running inside that will be down

and users will not be able to access them.

I know what you would be thinking.

How about doing high availability on

that, having multiple docker engine.

And you are right, we should be doing a clustering of

a docker engine if you are running it for production.

So not just one single docker node, multiple docker

nodes, but we will also need a master node

that is going to control all these docker nodes.

Sorry.

The master node will give instruction to

the docker node about containers to run.

It's going to distribute containers across your docker nodes

in case any of the docker node fails.

You can run containers on the live docker engines.

Or how about they get started

automatically on the docker engine.

Containers on the third node failed. Failed.

The node itself failed.

The containers migrated to the healthy node.

This itself is called as container orchestration.

You will have a master node,

which we call it as orchestrator.

And you will have cluster of docker nodes or

worker nodes where orchestrator will distribute the container.

So all your docker node will be one

single pool of resource which is fault tolerant.

Container orchestration is done mostly for

production environment, but you can run

normal containers also on them.

And today's time we have few

orchestration tools in the market.

We have docker swarm, it's from docker directly.

We have Kubernetes, the most famous

one, Mesosphere Marathon from Apache.

We have cloud based AWS ECS.

We have AWS EKS.

We have EKS again Elastic Kubernetes service, Azure.

We have Container service.

We have Google container engine Coros fleet OpenShift.

So you have cloudbased also.

You have inhouse solution also to

build your own orchestration platform.

Now, among all this, Kubernetes is the most famous

one and other technologies like EKS is actually Kubernetes.

And on Mesosphere Marathon you run Kubernetes cluster.

So most of the places Kubernetes is used, why?

A news from past from Google?

Back in 2014, Google announced that everything in

Google Gmail or everything runs on Linux containers.

And each week we launch more than 2 billion containers.

This was in 2014.

Now, when I saw this first time when I

was learning containers and when I was learning Kubernetes,

it was really a jaw dropping news for me.

I did not hear it in 2014, I got to know it later.

Jaw dropping because not of container, but because

of the number of containers, 2 billion containers.

But when I use the technology, I

understood why is that containers are disposable.

So any changes you want to make, we replace the

containers and imagine Google data center across the world.

Of course, there'll be managing billions of containers.

Now. That's a big news.

Everyone wanted to know how they are doing it.

So Kubernetes was created by Google.

Actually they created a tool known as

Borg to manage Linux container LXC

There was no Kubernetes worked back then.

But then in 2014, mid 2014, Google

introduced Kubernetes as an open source project,

which is just a version of Bark.

Then in mid 2015, Kubernetes stable

version was released V 10.

And also Google partnered with

CNCF Cloud Native Computing Foundation.

Now the project is managed by CNCF.

CNCF also has certification on

Kubernetes and training programs also

In 2016, Kubernetes goes mainstream.

There are tools that started getting

developed for it, like Kops, mini kube.

These are tools to create or

set up the Kubernetes cluster.

Then in late 2016, a case study was

released by Pokemon Go, which gave people more

confidence on running Kubernetes for production.

Then in 2017, the enterprise adoption came in Google.

IBM announced istio controller ingress controls

more like application load balancer.

GitHub started running on Kubernetes, oracle joined

CNCF, and the rest is history.

Now, I'm talking as if it

happened long, long time back.

It's just 2017.

It's just three years now.

Not even complete three years now.

Along with its mature platform, Google is using it.

Google was using it for decades now.

So, apart from all that Google power, there's

so many amazing feature that Kubernetes really provides.

First of all, Kubernetes really not

a replacement for docker engine.

Kubernetes manages the cluster of docker engine.

And not only docker engine, it can manage

cluster of other container runtime environment like rocket.

So, amazing features.

With Kubernetes, you have

service discovery, load balancing.

You create a container, which we call it a

spot here, which gets automatically discovered by the load

balancer, and it gets updated in the load balancer.

Also we'll see how cool is that?

Storage orchestration, kubernetes provide integration with

lots of storage, SAN, NAV, even

EBS volume, ceph storage.

And there's a huge list that goes on.

So people got more confident

on running stateful containers.

Now, automated Rollback it's very easy to roll

out a new image version and also roll

back very easily if it's not working.

Just like we do in beanstalk, but faster than that.

Automatic bin packing.

So it's going to place your container

on the right note where it gets

the right resource based on the requirement.

And because of that, your resource

is best utilized your computer resource.

Self Healing on Node we

already discussed orchestration tools.

If the node goes down, it brings your

containers to life on the live node.

Apart from that, your containers are also monitored.

You can set that just like Auto Scaling group.

When an instance goes down, Auto scaling

group will launch a replacement like that

The self healing capability, it's much

faster than Auto scaling group.

You can manage the configuration in form of variables

and volumes and also secrets which are encoded values.

There are actually many more things we can go on

and on but kind of highlighting cool features of Kubernetes.

You can check in the link

Kubernetes documentation and go through.

It's a nice overview.

Anyways, we are going to run through the documentation.

Also Kubernetes architecture.

So there are many services in play that gives

you the complete Kubernetes architecture or the cluster.

Two main components, master node and worker node.

Worker nodes are the one

where docker engine are running.

Master node is the one that

is managing these worker nodes.

So you don't log into the

worker node and run the containers.

You tell it to the master node.

You don't even log into master node.

You connect by using some client.

You give information to the master node that

I want to run so on so containers.

And it is going to take

the action based on the requirement.

So you have in the master node

which is also called as control plane.

Master node is also called as control plane.

You have service here, API server one service

second scheduler, third controller manager, fourth etcd.

These are four basic services.

Then you can add few more services.

There are add ons also.

But these are four primary service

in Kubernetes master or control plane.

Worker node will have kublet proxy, the docker engine.

These three important services running on worker node.

We'll understand all of this one by one.

First, let's talk about the control

plane, master node, kube API server.

The first service we will talk about and

this is the main hero in this game.

It handles all the incoming and outgoing communication.

This makes the communication possible

to and through Kubernetes cluster.

So when you want to send instructions to Kubernetes

kube API server is going to receive that.

And then it's going to pass the

information to other services like scheduler etcd.

And worker notes.

It exposes Kubernetes API.

If you want, you can build your own

tool that gets integrated with Kubernetes API.

There are so many third party tools to be

available to integrate with your Kubernetes API which you

can use like monitoring agent, logging agent, web dashboards.

It is the front end of the control plane or

for the whole Kubernetes cluster, that's the front end being

an admin or even DevOps in general admin.

We can use kubectl command line interface

to connect to the API server.

So we should have this kube

CTL installed in our machine.

We're going to use that and

connect it to the Kubernetes cluster.

There's actually a lot of commands and you

really need to master the art of Kubectl.

If you're managing Kubernetes cluster.

There's also web dashboard which you

can integrate with the API server.

And there are many more integrations.

Okay, that's API server first component

on our master node, second etcd.

Storage, etcd.

Is a key value store.

It stores the information of your Kubernetes cluster.

The kube API service going to store

or retrieve information from this, etc.

It will have all the runtime information

and it should be backed up regularly.

Because if this fails, you lose the current data.

You will not know what pod is

running, where the containers will be still

running, but you'll lose the information.

It stores the current state

of everything in the cluster.

Next is Scheduler.

Third component in our master node, scheduler is going

to schedule your container on the right node.

So it's going to watch for the request.

When it receives, Scheduler will pick up the right worker

node and send the information to the worker node saying

that, hey, you need to run this container.

And there are various factors based on which

it is going to decide, like based on

the resource requirement or the hardware software or

any policy that you have given.

Like you have said, I want to run it on

a worker node that has XYZ hardware or XYZ software.

So those factors will be considered

affinity and anti affinity rules.

You can say I want to run my container on

this particular node or just the opposite, I don't want

to run my container on this particular node.

Okay, that is also a factor date,

locality and there are few other factors.

So mostly automatically it will decide, but you can

also give the policy affinity or Nty affinity rules.

Okay.

Fourth component, controller Manager.

Actually it's group of multiple

things that are running.

So reduce the complexity.

We just call it as Controller Manager.

One single thing, but it actually does multiple things.

It's a node controller.

It's going to monitor your worker node.

If it goes down, it's going to take some actions.

Replication controller it has which is

going to monitor your pods.

Pods as of now, understand as container.

We'll get into what is parts.

Think of them as just container for now.

So replication controller is going to monitor your

containers and if it goes down, it's going

to do the auto hailing endpoint controller.

It's going to populate the endpoint

object which we're going to see.

There is service object and service account

and Token controller manages the authentication authorization.

Okay, so these were the

control plane master node component.

Let's check the worker node components.

Okay, first of all, you have

the kubelet, that is the agent.

It will be running on every node.

And this is going to listen to

your Kubernetes master request or commands.

So when Scheduler decides that this worker node

is going to run the container, it's going

to assign the responsibility to kubelet.

Now kubelet is going to fetch your

image and run the container from it.

So it's going to do the heavy lifting.

So as we run the commands

right, docker run -p -v .....

Now kubelet will be doing it kubeproxy.

This actually is a network proxy that is going

to run on every note in the cluster.

You can set network rules also like security group

rules, we have allow this or deny that.

And the most important

one, container runtime environment.

So you can have docker.

Now, Kubernetes is quite flexible in this.

You can have docker engine in that you

can have container D, you can have Rocket

or you can have Kubernetes CRI.

So if you go with docker swarm,

then you can only use docker engine.

But with Kubernetes you can

use other runtime environment also.

So, along with all these components, if you want,

you can do some add ons like DNS, web

UI, or resource monitoring, or cluster level logging.

Most of the time these components are taken by

some third party vendors who have some specialization in

that area, like better logging tool, better monitoring tool,

or web user interface, or even DNS service.

Okay, let's look at the architecture once again.

kubelet is our tool, which we are going to use

to connect to the Kubernetes master master mode, you have

APS server scheduler, controller manager at CD, etcd.

Stores the current information.

API server enables the communication scheduler, decides where

your container will be running on which node.

Controller manager responsible for monitoring

worker node, your containers, and

also the authentication authorization.

In worker node, you have kubelet, which is the agent.

Now, don't get confused between kubelet and kube CTL.

It's quite easy to confuse between them.

kubectl is our tool to connect, and kubelet is

an agent running in the work or not, right?

So, kubelet will do all the

heavy lifting on the container.

It's going to fetch the image, run the

containers, map the volumes, do all those stuff.

kube proxy is a network proxy.

If you want to expose a Pod to the

outside world, you can do it through Kube proxy,

or you can even set the network rules.

And then the docker engine, of course,

where your containers will be running, but

you see the container enclosed in Pod.

Okay, Pod, we'll understand what really is this Pod.

Now, what is the relation

between Pod and the container?

It's the same relation a VM has

with the process running inside it.

So let's say a Tomcat process is running in a VM.

So the VM is going to provide all the

resource to the process, which is running network, Ram,

CPU, storage, everything, and the process just uses it.

Similarly, Pod is going to provide

all the resource to a container.

The container will be running inside the Pod.

So container will be like the process

and Pod will be like the VM.

And I'm just giving you this

example so you can relate again.

There is no virtualization.

Here it's again isolation.

Now, why does Kubernetes use pod

Why not directly run containers?

Well, it's because Kubernetes can use different

container runtime environment like docker, rocket, CRI.

If you don't have the Pod,

there will be no abstraction.

Now, we have Pod.

It's a standard set of commands, standard set

of configuration that we do, it doesn't matter

what technology we are using behind the scene.

So Pod gives us an abstraction.

So we give information to the Pod, what to

do, and Pod is going to do it.

That for the container which is running inside it.

So if you're running a tomcat process in the Pod, the

Tomcat will be the container which will be running on port

8080 and the Pod will give the IP address.

So you can access it by giving the Pod

IP and the port number of the container.

We'll see how that works.

As of now, you can go with

the idea containers are inside the Pod.

And in a Pod you can have one or many container.

Pod gives the resources to the container.

So first you see Pod One, there's a

Pod and there's one container running inside that.

Second example you see Pod.

There's a container and there is

a volume attached to it.

Third example you see two containers and a volume.

Now in this case, both the containers

will have access to this volume.

So you can have one or

many containers running inside the Pod.

But should you run multiple containers inside the Pod?

Well, it really depends.

Ideally you will see one

container running inside the Pod.

The other container will be the helper containers.

So you see here in node one, you have

a Pod and a main container running inside that.

So one Pod, one container.

In the second example you see two containers.

One is called a sidecar.

The other one is in it.

Now in its container will be short lived container.

It's going to start does some command

execution and then it will be dead.

Then when it is dead, the main

container will start with the sidecar container.

If you have sidecar container, work will be helping

the main container, like for example, streaming the log.

So it could be a logging agent or

a monitoring agent to help your main container.

But at any given point of time, you should

have one main container only running in the Pod.

The other containers will be helper containers.

So my point is, if you have tomcat and MySQL, you

are not going to run both in the same pod.

You'll run it on different different pods.

Containers will be distributed across multiple and

now we will use the word Pod.

Pod will be distributed across multiple worker nodes.

So let's say you have a Pod One, which is

in node One and you have Pod Six, which is

in node three, and they want to interact.

Maybe Pod One is Tomcat, pod Six is MySQL.

So how will they interact?

Well, there is overlay network.

Think of this as the VPC that we have seen in AWS.

So you have a joint network, a virtual network

that connects all the node and every node.

You'll have a subnet, like a local area

network, a private network running inside the node.

And you see their bridge zero.

This will act like a switch.

So all the Pod running in this node,

one will be able to communicate with each

other with the help of this bridge zero.

But when it wants to connect to a container to

a Pod running in another node, then bridge zero is

going to forward the request to this WG zero.

You see, that acts like a router.

So it's going to route by looking at the IP address,

it's going to route it to the right node router.

So it receives by the other router in

the node that forwards it to the switch.

And then the switch sends it to the Pod.

Now I'm using the word

switch and router for understanding.

So there will be a joint network, virtual network.

All your Pod doesn't matter in what node

it is, will be in that network.

Every node will have a small private network.

And all these private network will

be connected in one bigger network.

This is overly network.

Okay, enough said about the architecture.

Let's see how to set up a Kubernetes Cluster now.

So Kubernetes Cluster can be set up

manually, which is the hardest way.

And frankly, you really don't need to do that if

you want to do it for understanding and understanding only.

If you really want to set up Kubernetes

Cluster, there are nice tools to do it.

You have mini kube to start with,

which is for testing and learning purpose.

It is just going to set one

node Kubernetes Cluster mostly in your computer.

So it's going to launch a virtual machine using

VirtualBox and on that one VM, the master node

and worker node components will be running only for

testing and learning purpose, not really production.

kubeadm is a very popular tool to

set up Kubernetes Cluster for production.

Multi node, Kubernetes cluster.

So you can have as many as worker node.

Let's say you're saying I need four

worker node and one master node.

So you need to log into master mode, run

some command, get into worker node, run some command,

and then they are finally connected together.

So you can use any platform if you're

using kubeadm, you want to do for easy

to physical machines, virtual machines anywhere.

There are a lot of manual steps over

here that you need to execute kops.

I find this is the most stable

way of running Kubernetes Cluster for production.

So it came initially only for AWS,

but now it has support also for

Google Cloud, Digital Ocean, and Open Stack.

So if you want to run your own cluster, kubernetes

Cluster the most stable way you can use kops.

So we're going to see we're going

to see mini kube and kops both way.

