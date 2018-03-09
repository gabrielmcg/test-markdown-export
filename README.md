 Page title here

# Introduction

HPE Enterprise Containers as a Service with Docker Enterprise Edition \(EE\) is a complete solution from Hewlett Packard Enterprise that includes all the hardware, software, professional services, and support you need to deploy a containers-as-a-service \(CaaS\) platform, allowing you to get up and running quickly and efficiently. The solution takes the HPE Synergy infrastructure and combines it with Docker’s enterprise-grade container platform, popular open source tools, along with deployment and advisory services from HPE Pointnext.

<table cellpadding="4" cellspacing="0" summary="" id="vcpu__vcpu-table" class="table" frame="border" border="1" rules="all"><caption><span class="tablecap"><span class="table--title-label">Table 1. </span>vCPU</span></caption><colgroup><col /><col /><col /><col /></colgroup>
<thead class="thead" style="text-align:left;">
<tr class="row">
<th class="entry nocellnorowborder" style="vertical-align:top;" id="d30e52">
<p class="p">vCPUs</p>

</th>

<th class="entry nocellnorowborder" style="vertical-align:top;" id="d30e58">
<p class="p">node01</p>

</th>

<th class="entry nocellnorowborder" style="vertical-align:top;" id="d30e64">
<p class="p">node02</p>

</th>

<th class="entry cell-norowborder" style="vertical-align:top;" id="d30e70">
<p class="p">node03</p>

</th>

</tr>

</thead>
<tbody class="tbody">
<tr class="row">
<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e52 ">
<p class="p">ucp1</p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e58 ">
<p class="p">4</p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e64 ">
<p class="p"></p>

</td>

<td class="entry cell-norowborder" style="vertical-align:top;" headers="d30e70 ">
<p class="p"></p>

</td>

</tr>

<tr class="row">
<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e52 ">
<p class="p">ucp2</p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e58 ">
<p class="p"></p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e64 ">
<p class="p">4</p>

</td>

<td class="entry cell-norowborder" style="vertical-align:top;" headers="d30e70 ">
<p class="p"></p>

</td>

</tr>

<tr class="row">
<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e52 ">
<p class="p">ucp3</p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e58 ">
<p class="p"></p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e64 ">
<p class="p"></p>

</td>

<td class="entry cell-norowborder" style="vertical-align:top;" headers="d30e70 ">
<p class="p">4</p>

</td>

</tr>

<tr class="row">
<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e52 ">
<p class="p">dtr1</p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e58 ">
<p class="p">2</p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e64 ">
<p class="p"></p>

</td>

<td class="entry cell-norowborder" style="vertical-align:top;" headers="d30e70 ">
<p class="p"></p>

</td>

</tr>

<tr class="row">
<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e52 ">
<p class="p">dtr2</p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e58 ">
<p class="p"></p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e64 ">
<p class="p">2</p>

</td>

<td class="entry cell-norowborder" style="vertical-align:top;" headers="d30e70 ">
<p class="p"></p>

</td>

</tr>

<tr class="row">
<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e52 ">
<p class="p">dtr3</p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e58 ">
<p class="p"></p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e64 ">
<p class="p"></p>

</td>

<td class="entry cell-norowborder" style="vertical-align:top;" headers="d30e70 ">
<p class="p">2</p>

</td>

</tr>

<tr class="row">
<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e52 ">
<p class="p">worker1</p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e58 ">
<p class="p">4</p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e64 ">
<p class="p"></p>

</td>

<td class="entry cell-norowborder" style="vertical-align:top;" headers="d30e70 ">
<p class="p"></p>

</td>

</tr>

<tr class="row">
<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e52 ">
<p class="p">worker2</p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e58 ">
<p class="p"></p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e64 ">
<p class="p">4</p>

</td>

<td class="entry cell-norowborder" style="vertical-align:top;" headers="d30e70 ">
<p class="p"></p>

</td>

</tr>

<tr class="row">
<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e52 ">
<p class="p">worker3</p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e58 ">
<p class="p"></p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e64 ">
<p class="p"></p>

</td>

<td class="entry cell-norowborder" style="vertical-align:top;" headers="d30e70 ">
<p class="p">4</p>

</td>

</tr>

<tr class="row">
<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e52 ">win-worker1</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e58 ">4</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e64 "> </td>

<td class="entry cell-norowborder" style="vertical-align:top;" headers="d30e70 "> </td>

</tr>

<tr class="row">
<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e52 ">win-worker2</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e58 "> </td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e64 ">4</td>

<td class="entry cell-norowborder" style="vertical-align:top;" headers="d30e70 "> </td>

</tr>

<tr class="row">
<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e52 ">win-worker3</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e58 "> </td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e64 "> </td>

<td class="entry cell-norowborder" style="vertical-align:top;" headers="d30e70 ">4</td>

</tr>

<tr class="row">
<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e52 ">
<p class="p">ucb_lb</p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e58 ">
<p class="p">2</p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e64 ">
<p class="p"></p>

</td>

<td class="entry cell-norowborder" style="vertical-align:top;" headers="d30e70 ">
<p class="p"></p>

</td>

</tr>

<tr class="row">
<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e52 ">
<p class="p">dtr_lb</p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e58 ">
<p class="p"></p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e64 ">
<p class="p">2</p>

</td>

<td class="entry cell-norowborder" style="vertical-align:top;" headers="d30e70 ">
<p class="p"></p>

</td>

</tr>

<tr class="row">
<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e52 ">
<p class="p">worker_lb</p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e58 ">
<p class="p"></p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e64 ">
<p class="p"></p>

</td>

<td class="entry cell-norowborder" style="vertical-align:top;" headers="d30e70 ">
<p class="p">2</p>

</td>

</tr>

<tr class="row">
<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e52 ">
<p class="p">nfs</p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e58 ">
<p class="p"></p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e64 ">
<p class="p"></p>

</td>

<td class="entry cell-norowborder" style="vertical-align:top;" headers="d30e70 ">
<p class="p">2</p>

</td>

</tr>

<tr class="row">
<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e52 ">
<p class="p">logger</p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e58 ">
<p class="p"></p>

</td>

<td class="entry nocellnorowborder" style="vertical-align:top;" headers="d30e64 ">
<p class="p">2</p>

</td>

<td class="entry cell-norowborder" style="vertical-align:top;" headers="d30e70 ">
<p class="p"></p>

</td>

</tr>

<tr class="row">
<td class="entry row-nocellborder" style="vertical-align:top;" headers="d30e52 ">
<p class="p">Total vCPU per node</p>

</td>

<td class="entry row-nocellborder" style="vertical-align:top;" headers="d30e58 ">
<p class="p">12</p>

</td>

<td class="entry row-nocellborder" style="vertical-align:top;" headers="d30e64 ">
<p class="p">14</p>

</td>

<td class="entry cellrowborder" style="vertical-align:top;" headers="d30e70 ">
<p class="p">14</p>

</td>

</tr>

</tbody>
</table>



