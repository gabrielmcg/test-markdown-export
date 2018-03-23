# Introduction

HPE Enterprise Containers as a Service with Docker Enterprise Edition \(EE\) is a complete solution from Hewlett Packard Enterprise that includes all the hardware, software, professional services, and support you need to deploy a containers-as-a-service \(CaaS\) platform, allowing you to get up and running quickly and efficiently. The solution takes the HPE Synergy infrastructure and combines it with Docker’s enterprise-grade container platform, popular open source tools, along with deployment and advisory services from HPE Pointnext.

HPE Enterprise Containers as a Service with Docker EE is ideal for customers migrating legacy applications to containers, transitioning to a container DevOps development model or needing a hybrid environment to support container and non-containerized applications on a common VM platform. HPE Enterprise Containers as a Service with Docker EE provides a solution for IT operations, addressing the need to have a production ready environment that is very easy to deploy and manage.

This document describes the best practices for deploying and operating HPE Enterprise Containers as a Service with Docker EE. It describes how to automate the provisioning of the environment using a set of Ansible playbooks. It also outlines a set of manual steps to harden, secure and audit the overall status of the system.

**Note:** 

The Ansible playbooks described in this document are only intended for Day 0 deployment automation of Docker EE on HPE Synergy.

The Ansible playbooks described in this document are not directly supported by HPE and are intended as an example of deploying Docker EE on HPE Synergy. We welcome input from the user community via GitHub to help us prioritize all future bug fixes and feature enhancements.

## About Ansible

Ansible is an open-source automation engine that automates software provisioning, configuration management and application deployment.

As with most configuration management software, Ansible has two types of servers: the controlling machine and the nodes. A single controlling machine orchestrates the nodes by deploying modules to the nodes over SSH. The modules are temporarily stored on the nodes and communicate with the controlling machine through a JSON protocol over the standard output. When Ansible is not managing nodes, it does not consume resources because no daemons or programs are executing for Ansible in the background. Ansible uses one or more inventory files to manage the configuration of the multiple nodes in the system.

In contrast with other popular configuration management software, such as Chef, Puppet, and CFEngine, Ansible uses an agentless architecture. With an agent-based architecture, nodes must have a locally installed daemon that communicates with a controlling machine. With an agentless architecture, nodes are not required to install and run background daemons to connect with a controlling machine. This type of architecture reduces the overhead on the network by preventing the nodes from polling the controlling machine.

More information about Ansible can be found at: [http://docs.ansible.com](http://docs.ansible.com/)

## About Docker Enterprise Edition

Docker Enterprise Edition \(EE\) is a leading enterprise containers-as-a-service \(CaaS\) software platform for IT that manages and secures diverse applications across disparate infrastructure, both on-premises and in the cloud. Docker EE provides integrated container management and security from development to production. Enterprise-ready capabilities like multi-architecture orchestration and secure software supply chain give IT teams the ability to manage and secure containers without breaking the developer experience.

Docker EE provides:

-    Integrated management of all application resources from a single web admin UI. 
-    Frictionless deployment of applications and Compose files to production in a few clicks. 
-    Multi-tenant system with granular role-based access control \(RBAC\) and LDAP/AD integration. 
-    Self-healing application deployment with the ability to apply rolling application updates. 
-    End-to-end security model with secrets management, image signing and image security scanning. 

More information about Docker Enterprise Edition can be found at: [https://www.docker.com/enterprise-edition](https://www.docker.com/enterprise-edition)

## HPE Synergy

HPE Synergy, the first platform built from the ground up for composable infrastructure, empowers IT to create and deliver new value instantly and continuously. This single infrastructure reduces operational complexity for traditional workloads and increases operational velocity for the new breed of applications and services. Through a single interface, HPE Synergy composes compute, storage and fabric pools into any configuration for any application. It also enables a broad range of applications from bare metal to virtual machines to containers, and operational models like hybrid cloud and DevOps. HPE Synergy enables IT to rapidly react to new business demands.

HPE Synergy Frames contain a management appliance called the HPE Synergy Composer which hosts HPE OneView. HPE Synergy Composer manages the composable infrastructure and delivers:

-    Fluid pools of resources, where a single infrastructure of compute, storage and fabric boots up ready for workloads and demonstrates self-assimilating capacity. 
-    Software-defined intelligence, with a single interface that precisely composes logical infrastructures at near-instant speeds; and demonstrates template-driven, frictionless operations. 
-    Unified API access, which enables simple line-of-code programming of every infrastructure element; easily automates IT operational processes; and effortlessly automates applications through infrastructure deployment. 

# Architecture

By default, the Ansible Playbooks will set up a 3 node environment. HPE and Docker recommend a minimal starter configuration of 3 physical nodes for running Docker in production. This is the minimal configuration that Docker recommends for cluster HA. The distribution of the Docker and non-Docker modules over the 3 physical nodes via virtual machines \(VMs\) is as follows:

-    3 Docker Universal Control Plane \(UCP\) VM nodes for HA and cluster management 
-    3 Docker Trusted Registry \(DTR\) VM nodes for HA of the container registry 
-    3 Docker Swarm Linux worker VM nodes for container workloads 
-    3 Docker Swarm Windows worker VM nodes for container workloads 
-    1 Docker UCP load balancer VM to ensure access to UCP in the event of a node failure 
-    1 Docker DTR load balancer VM to ensure access to DTR in the event of a node failure 
-    1 Docker Swarm Worker node VM load balancer 
-    1 Logging server VM for central logging 
-    1 NFS server VM for storage Docker DTR images 

In addition to the above, the playbooks also set up:

-    Docker persistent storage driver from VMware 
-    Prometheus and Grafana monitoring tools 

These nodes can live in any of the hosts and they are not redundant. The Prometheus and Grafana services are declared in a Docker stack as replicated services with one replica each, so if they fail, Docker EE will ensure that they are restarted on one of the UCP VMs. cAdvisor and node-exporter are declared in the same stack as global services, so Docker EE will ensure that there is always one copy of each running on every machine in the cluster. The vSphere Docker volume plug-in stores data in a shared datastore that can be accessed from any machine in the cluster.

## Server requirements:

Two platforms will be described / tested:

1.  3 node HPE Synergy 480 Gen10 deployment with 1 node in each Synergy frame 
    -    384 GB DDR4-2133 RAM 
    -    2 Intel Xeon CPU Gold 6130 2.10GHz x 16 core 
    -    single ESXi cluster with control plane and docker workers spread out on all 3 nodes 
2.  6 node HPE Synergy 480 Gen 10 deployment with 2 nodes in each Synergy frame 
    -    384GB DDR4-2133 RAM 
    -    2 Intel Xeon CPU Gold 6130 2.10GHz x 16 core 
    -    single ESXi cluster with control plane on 3 nodes and 3 nodes dedicated as Docker workers \(should this be 2 clusters?\) 

TBD: How many workers should be deployed on a single ESXi host dedicated to Docker workers to maximize use of the server and justify the cost of VMware license.

## Storage requirements:

3PAR store required for ESXi datastore \(block storage\)

Currently have 8x 480GB SSD used for datastore

NFS storage - TBD, this needs file persona enabled

will need additional storage for File Persona

![ "HPE Synergy Solution"][media-architecture1-png]

**Figure 1.** HPE Synergy Solution

![ "HPE Synergy Solution"][media-architecture2-png]

**Figure 2.** HPE Synergy Solution

## High availability

Uptime is paramount for any users implementing Docker containers in business critical environments. HPE Enterprise Containers with Docker EE offers various levels of high availability \(HA\) to support continuous availability. All containers including the Docker system containers are protected by Docker’s swarm mode. Swarm mode can protect against individual hardware, network, and container failures based on the user’s declarative model. The Ansible playbooks can be modified to fit your environment and your high availability \(HA\) needs.

### Load Balancers

HPE Enterprise Containers with Docker EE also deploys load balancers in the system to help with container traffic management. There are three load balancer VMs – UCP load balancer, DTR load balancer, and Docker worker node load balancer. Since these load balancers exist in VMs, they have some degree of HA but may incur some downtime during the restoration of these VMs due to a planned or unplanned outage. For optimal HA configuration, the user should consider implementing a HA load balancer architecture using the Virtual Router Redundancy Protocol \(VRRP\). For more information see [http://www.haproxy.com/solutions/high-availability/](http://www.haproxy.com/solutions/high-availability/).

 ![ "Load balancer architecture"][media-load-balancers-png] 

**Figure 3.** Load balancer architecture



[media-architecture1-png]:</media/architecture1.png> "Figure 1. HPE Synergy Solution"
[media-architecture2-png]:</media/architecture2.png> "Figure 2. HPE Synergy Solution"
[media-load-balancers-png]:</media/load-balancers.png> "Figure 3. Load balancer architecture"
[media-provisioning-png]:</media/provisioning.png> "Figure 4. Provisioning steps"
[media-create-volume-png]:</media/create-volume.png> "Figure 5. Create volume"
