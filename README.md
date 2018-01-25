# Page title here

## Introduction

HPE Enterprise Containers as a Service with Docker Enterprise Edition \(EE\) is a complete solution from Hewlett Packard Enterprise that includes all the hardware, software, professional services, and support you need to deploy a containers-as-a-service \(CaaS\) platform, allowing you to get up and running quickly and efficiently. The solution takes the HPE Synergy infrastructure and combines it with Docker’s enterprise-grade container platform, popular open source tools, along with deployment and advisory services from HPE Pointnext.

HPE Enterprise Containers as a Service with Docker EE is ideal for customers migrating legacy applications to containers, transitioning to a container DevOps development model or needing a hybrid environment to support container and non-containerized applications on a common VM platform. HPE Enterprise Containers as a Service with Docker EE provides a solution for IT operations, addressing the need to have a production ready environment that is very easy to deploy and manage.

This document describes the best practices for deploying and operating HPE Enterprise Containers as a Service with Docker EE. It describes how to automate the provisioning of the environment using a set of Ansible playbooks. It also outlines a set of manual steps to harden, secure and audit the overall status of the system.

 **Note:** 

-   The Ansible playbooks described in this document are only intended for Day 0 deployment automation of Docker EE on HPE Synergy.
-   The Ansible playbooks described in this document are not directly supported by HPE and are intended as an example of deploying Docker EE on HPE Synergy. We welcome input from the user community via GitHub to help us prioritize all future bug fixes and feature enhancements.

### About Ansible

Ansible is an open-source automation engine that automates software provisioning, configuration management and application deployment.

As with most configuration management software, Ansible has two types of servers: the controlling machine and the nodes. A single controlling machine orchestrates the nodes by deploying modules to the nodes over SSH. The modules are temporarily stored on the nodes and communicate with the controlling machine through a JSON protocol over the standard output. When Ansible is not managing nodes, it does not consume resources because no daemons or programs are executing for Ansible in the background. Ansible uses one or more inventory files to manage the configuration of the multiple nodes in the system.

In contrast with other popular configuration management software, such as Chef, Puppet, and CFEngine, Ansible uses an agentless architecture. With an agent-based architecture, nodes must have a locally installed daemon that communicates with a controlling machine. With an agentless architecture, nodes are not required to install and run background daemons to connect with a controlling machine. This type of architecture reduces the overhead on the network by preventing the nodes from polling the controlling machine.

More information about Ansible can be found at: [http://docs.ansible.com](http://docs.ansible.com/)



<table class="table frame-all" id="d1e33__table_cj5_llk_tt"><caption></caption><colgroup><col><col></colgroup><thead class="thead">
                <tr class="row">
                    <th class="entry colsep-1 rowsep-1" id="d1e33__table_cj5_llk_tt__entry__1">Key</th>
                    <th class="entry colsep-1 rowsep-1" id="d1e33__table_cj5_llk_tt__entry__2">Value Descriptions</th>
                </tr>
            </thead><tbody class="tbody">
                <tr class="row">
                    <td class="entry colsep-1 rowsep-1" headers="d1e33__table_cj5_llk_tt__entry__1 ">mode</td>
                    <td class="entry colsep-1 rowsep-1" headers="d1e33__table_cj5_llk_tt__entry__2 ">Specifies the bonding policy. Possible values are: <ul class="ul">
                        <li class="li">balance-rr - Transmit packets in sequential order from the first available
                            slave through the last.</li>
                        <li class="li">active-backup - Only one slave in the bond is active. A different slave
                            becomes active if, and only if, the active slave fails.</li>
                        <li class="li">balance-xor - Transmit based on the selected transmit hash policy.</li>
                        <li class="li">broadcast - Transmits everything on all slave interfaces.</li>
                        <li class="li">802.3ad - IEEE 802.3ad Dynamic link aggregation.</li>
                        <li class="li">balance-tlb - Adaptive transmit load balancing: channel bonding that does not
                            require any special switch support.</li>
                        <li class="li">balance-alb - Adaptive load balancing: includes balance-tlb plus receive load
                            balancing (rlb) for IPV4 traffic and does not require any special switch
                            support.</li>
                    </ul>
                    </td>
                </tr>
                <tr class="row">
                    <td class="entry colsep-1 rowsep-1" headers="d1e33__table_cj5_llk_tt__entry__1 ">miimon</td>
                    <td class="entry colsep-1 rowsep-1" headers="d1e33__table_cj5_llk_tt__entry__2 ">Specifies the MII link monitoring frequency in milliseconds. This determines
                        how often the link state of each slave is inspected for link failures. Accepts
                        values in milliseconds.</td>
                </tr>
                <tr class="row">
                    <td class="entry colsep-1 rowsep-1" headers="d1e33__table_cj5_llk_tt__entry__1 ">primary</td>
                    <td class="entry colsep-1 rowsep-1" headers="d1e33__table_cj5_llk_tt__entry__2 ">The device to use as the primary when the mode is one of the possible values
                        below: <ul class="ul">
                            <li class="li">active-backup</li>
                            <li class="li">balance-tlb</li>
                            <li class="li">balance-alb</li>
                        </ul></td>
                </tr>
            </tbody></table>				


