---
layout: static
---

<div style="text-align:center; padding: 20px; font-size: 16px; font-weight: bold;">
<div style="padding: 20px;">Meet Pixie. Our first prototype.</div>
<img style="border-radius: 20px;" src="images/mini-HPC-proto1.png" width="600px">
</div>
<div>
<h2>What?</h2>
Pixie is our prototype High Performance Computer (HPC), built with:

<ul>
	<li>Raspberry Pi (RPi) 4 2GB single board computers (SBC).</li>
	<li>An 8 port Netgear switch</li>
	<li>A 128GB flash drive for shared storage</li>
	<li>A 32GB SD card to boot the main node from</li>
	<li>A very expensive, highly specilized cooling device to keep it all cool. (Oh, okay then, it's a USB desktop fan)</li>
	<li>Loads of power supplies</li>
	<li>Loads of 10BaseT Cat6 ethernet cables</li>
	<li>3D printed DIN Rail stand</li>
	<li>3D printed RPi cases</li>
	<li>Strip plug</li>
</ul>

<h2>Why?</h2>
There are two parts to the why. 1) Why RPis when we have already mentioned that they are almost impossible to get hold of and 2) why a mini HPC?

<h3>Why Pi?</h3>
Because RPis are nowhere to be found, the decision was made to buy Rock 4SE SBCs. The problems is that these boards are only available at two companies in the UK, RS and OKdo, and OKdo is a subsidiary of RS. We noticed that they have discounts available for education so we started an enquiry into the possibility of getting these discounts. Unfortunately this is where the wheels came off. It took three weeks before we could eventually place an order and when the last batch of items, the PoE hats, arrived, they didn't fit the Rock 4 boards. While this was going on, to not waste time, we started putting together a mini-HPC using Raspberry Pis that we already own.

<h3>Why a mini HPC?</h3>
Many people have built Raspberry Pi HPCs, why do we want to include this as part of the CarpentriesOffline project. The need for this project became apparent in February 2023 when we ran a workshop for the N8 at Newcastle University using the Carpentries Incubator lesson, Introduction to High-Performance Computing. There are a few things that seem to, almost always, go wrong when running a workshop such as this one:

<ol>
	<li>People do not register for HPC accounts before the workshop. Most HPCs will have certain hoops you need to jump through when you want to obtain a user account on them. There are often time delays to get the accounts approved which means that if the learners did not obtain their logins before the workshop they are not guaranteed to get a login arranged on the day of the workshop.</li>
	<li>Login nodes can experience problems due to users running processes on them that they are not supposed to. When this happens others users cannot log in. Obviously, workshop have to happen within a certain time frame and if the learners can get logged in, the workshop can't continue.</li>
	<li>The length of queues and the load on an HPC cannot be controlled and if it so happens that many other users are accessing the HPC on the day of the workshop, access can be slow and jobs in the queue might not get completed in a timely manner for the workshop.</li>
	<li>Last but not the least are problems with The Internet itself.</li>
</ol>

HPCs are not easy to set up. Many document their processes but it still requires quite a lot of expertise to set up. What we would like to do is to create images of the SD cards required to boot the RPis and/or Rock Pis straight into an HPC. Instructors should be able to obtain specified hardware and know how to connect everything, write the OS image to an SD card or SSD and boot the computer into a usable HPC state.

<h3>Current Unknowns and Testing</h3>
We need to test this system prior to using it in a workshop with learners. It may also be sensible to use it initially with a backup option of learners having accounts on an existing HPC system in case of failures. Current questions we have include:
	
<ol>
	<li><strong>How reliable is a Pi HPC?</strong> Workshops commonly include between 20 and 40 learners. Raspberry Pis are relatively low-spec machines, especially if using the first, second and third generation models, rather than the latest Pi4s. There's an open question about how many simultaneous users a Pi-based login node can support.</li>
	<li><strong>Can our DHCP server support that many users?</strong> The default CIDR/24 block of 192.168.1.1 to 192.168.1.254 has enough IP addresses for 255 external clients, but in practice client limits and the memory requirements of managing them (especially on a Pi) can lead to address assignment failures.</li>
	<li><strong>Can the Pi's WiFi interface handle the required traffic?</strong> Related to the above, there's an open question as to whether the Pi will handle having 40+ clients connected through the WiFi interface.</li>
	<li><strong>How many Pi nodes do we need in a cluster to handle all the Slurm jobs that will be queued and launched?</strong> This is also a relevant question for anyone implementing the Pi HPC in a Carpentries Offline lesson, as for cost-effectiveness, we should provide an estimate connecting the number of nodes to the number of learners.</li>
	<li><strong>Will we need multiple login nodes?</strong> If a single login node slows down too much with too many learners connected, it may be necessary to create another login node.</li>
	<li><strong>Will there be a bottleneck in the shared storage USB?</strong> USB Shared storage can become bottlenecked under high resource use. Earlier generations than the Raspberry Pi 4 were restricted by USB-2's 480 Mbps limit. Some testing of throughput should be conducted. An <a href="https://www.tomshardware.com/news/raspberry-pi-4-ssd-test,39811.html">external SSD</a> could potentially be faster than USB storage.</li>
</ol>

</div>
