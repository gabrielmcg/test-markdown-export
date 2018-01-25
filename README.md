
# test page


		<h2 class="title topictitle2" id="ariaid-title2">Introduction</h2>

		<div class="body">
			<p class="p">HPE Enterprise Containers as a Service with Docker Enterprise Edition (EE) is a complete solution from Hewlett Packard Enterprise that includes all the hardware, software, professional services, and support you need to deploy a containers-as-a-service (CaaS) platform, allowing you to get up and running quickly and efficiently. The solution takes the HPE Synergy infrastructure and combines it with Docker’s enterprise-grade container platform, popular open source tools, along with deployment and advisory services from HPE Pointnext.</p>

			<p class="p">HPE Enterprise Containers as a Service with Docker EE is ideal for customers migrating legacy applications to containers, transitioning to a container DevOps development model or needing a hybrid environment to support container and non-containerized applications on a common VM platform. HPE Enterprise Containers as a Service with Docker EE provides a solution for IT operations, addressing the need to have a production ready environment that is very easy to deploy and manage.</p>

			<p class="p">This document describes the best practices for deploying and operating HPE Enterprise Containers as a Service with Docker EE. It describes how to automate the provisioning of the environment using a set of Ansible playbooks. It also outlines a set of manual steps to harden, secure and audit the overall status of the system.</p>

			<p class="p">
				<strong class="ph b">Note:</strong>
			</p>

			<ul class="ul">
				<li class="li">The Ansible playbooks described in this document are only intended for Day 0 deployment automation of Docker EE on HPE Synergy.</li>

				<li class="li">The Ansible playbooks described in this document are not directly supported by HPE and are intended as an example of deploying Docker EE on HPE Synergy. We welcome input from the user community via GitHub to help us prioritize all future bug fixes and feature enhancements.</li>

			</ul>

		</div>

		<div class="topic nested2" aria-labelledby="ariaid-title3" id="d1e33">
			<h3 class="title topictitle3" id="ariaid-title3">About Ansible</h3>

			<div class="body">
				<p class="p">Ansible is an open-source automation engine that automates software provisioning, configuration management and application deployment.</p>

				<p class="p">As with most configuration management software, Ansible has two types of servers: the controlling machine and the nodes. A single controlling machine orchestrates the nodes by deploying modules to the nodes over SSH. The modules are temporarily stored on the nodes and communicate with the controlling machine through a JSON protocol over the standard output. When Ansible is not managing nodes, it does not consume resources because no daemons or programs are executing for Ansible in the background. Ansible uses one or more inventory files to manage the configuration of the multiple nodes in the system.</p>

				<p class="p">In contrast with other popular configuration management software, such as Chef, Puppet, and CFEngine, Ansible uses an agentless architecture. With an agent-based architecture, nodes must have a locally installed daemon that communicates with a controlling machine. With an agentless architecture, nodes are not required to install and run background daemons to connect with a controlling machine. This type of architecture reduces the overhead on the network by preventing the nodes from polling the controlling machine.</p>

				<p class="p">More information about Ansible can be found at: <a class="xref" href="http://docs.ansible.com/" target="_blank">http://docs.ansible.com</a></p>

				<p class="p"></p>

				<p class="p"></p>

				

<div class="tablenoborder"><table cellpadding="4" cellspacing="0" summary="" id="d1e33__table_cj5_llk_tt" class="table" frame="border" border="1" rules="all"><colgroup><col /><col /></colgroup><thead class="thead" style="text-align:left;">
                <tr class="row">
                    <th class="entry cellrowborder" style="vertical-align:top;" id="d30e89">Key</th>

                    <th class="entry cellrowborder" style="vertical-align:top;" id="d30e92">Value Descriptions</th>

                </tr>

            </thead>
<tbody class="tbody">
                <tr class="row">
                    <td class="entry cellrowborder" style="vertical-align:top;" headers="d30e89 ">mode</td>

                    <td class="entry cellrowborder" style="vertical-align:top;" headers="d30e92 ">Specifies the bonding policy. Possible values are: <ul class="ul">
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
                    <td class="entry cellrowborder" style="vertical-align:top;" headers="d30e89 ">miimon</td>

                    <td class="entry cellrowborder" style="vertical-align:top;" headers="d30e92 ">Specifies the MII link monitoring frequency in milliseconds. This determines
                        how often the link state of each slave is inspected for link failures. Accepts
                        values in milliseconds.</td>

                </tr>

                <tr class="row">
                    <td class="entry cellrowborder" style="vertical-align:top;" headers="d30e89 ">primary</td>

                    <td class="entry cellrowborder" style="vertical-align:top;" headers="d30e92 ">The device to use as the primary when the mode is one of the possible values
                        below: <ul class="ul">
                            <li class="li">active-backup</li>

                            <li class="li">balance-tlb</li>

                            <li class="li">balance-alb</li>

                        </ul>
</td>

                </tr>

            </tbody>
</table>
</div>
				
				
			</div>

		</div>

	</div>
