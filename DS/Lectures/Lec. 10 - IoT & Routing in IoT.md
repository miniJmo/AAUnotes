# IoT
* Wireless sensor network: is it still important?
	* we are now focused on IoT
	* knowledge about WSN helps in understanding IoT

## Sensors
* we want to monitor
	* spaces
	* Things
	* Interactions 

* random  microcontrollers ![[Pasted image 20231123125149.png]]


## Energy 
* energy consumption of a phone (2005)![[Pasted image 20231123125307.png]]

* Dynamic power management (DPM)
	* Example: STRONGARM SA1100
		* *RUN*: Operational 
		* *IDLE*: a SW routing may stop the CPU when not in use, while monitoring interrupts 
		* *SLEEP*: Shutdown of on-chip activity ![[Pasted image 20231123125532.png]]
		* Idle is faster to start running again compared to sleep, but sleep is more power efficient 

## Sample Applications

## Mainstream protocols / MAC layers
* Standardised WSN protocols 
	* “Traditional WiFi + IP” too resource intensive for WSN
	* 802.15.1 (Bluetooth: cable replacement)
		* 1 PAN coordinator + up to 7 slaves
		* Version 1.0 …4.x now 5.0
		* BLE a.k.a. Bluetooth SMART
		* Bluetooth Mesh![[Pasted image 20231123130442.png]]

* Personal area networks 
	* 802.15.4 designed for wireless personal area networks (home automation, cars, remote metering,…)
		* Monitoring and Control
		* Ease of installation, but no mobility
		* Low power (protocol assumes that nodes sleep most of the time)
		* Low transmission rates (<250kbps), low range (<75m max.)
	* 802.15.4 defines Physical and MAC layer. What to run on top of it?![[Pasted image 20231123130728.png]]

* IEEE 802.15.4 MAC Overview ![[Pasted image 20231123131129.png]]

* MAC Topology![[Pasted image 20231123131205.png]]

* Hidden node problem: CSMA-CA![[Pasted image 20231123131442.png]]

* IEEE 802.15.4 MAC Overview
	* Optional Superframe Structure![[Pasted image 20231123131533.png]]

* MAC Modes![[Pasted image 20231123132108.png]]

* Zigbee
	* Defines Network layer on top of 802.15.4
	* Developed by the Zigbee alliance
	* Nodes can join a network, get a 16bit address assigned
	* Routing algorithm for tree (and star) and mesh topologies
	* Route discovery based on distance vector algorithm
	* 128-bit AES encryption
	* Also provides an application layer framework for applications![[Pasted image 20231123132207.png]]

* 6LoWPAN
	* “Why invent a new protocol when we already have IP?”
		* Developers are familiar with IP
		* 16 bit addresses (ZigBee) not enough for the Internet of Things
	* Developed by IETF: 6LowPan: IPv6 over 802.15.4![[Pasted image 20231123132639.png]]
	* Stacked headers
		* Basic header for small packets sent point-to-point or in star networks: 4 bytes (!)
			* 802.15.4 MAC addresses are 64bit long (in the MAC frame)
			* In IPv6, the lower 64bit (of 128 bits) can be the MAC’s address
			-> No need to repeat address in 6LowPan header (compressed header)
		* Optional Fragmentation header for large packets
		* Optional Mesh Networking header for mesh networks![[Pasted image 20231123132749.png]]

* LoRa - Long Range
	* Long-range, low-power and low-throughput
	* It is very slow
	* LoRa: PHY layer, developed by Semtech
	* LoRaWAN MAC layer defined by LoRaAlliance
	* Range:
		* 2-5 km in urban environments
		* >15 km in open space
	* Throughput: 0.3 kbps to 50 kbps
	* LoRaWAN MAC adapts Spreading Factor (SF) of PHY to balance data rate / range / lifetime                                                                  ![[Pasted image 20231123132934.png]]

* SigFox
	* Very long range (a few km in cities, up to 40km in rural areas with directional antennas)
	* The signal can reach underground objects.
	* Sigfox deploys its antennas with the help of local telcos around the world
		* Thus Sigfox itself takes care of coverage
		* Device owners pay a subscription (1 Euro per device per year)![[Pasted image 20231123133042.png]]

 * NB-IoT (Narrowband Internet of Things)
	 * Narrowband Internet of Things (NB-IoT) is a secure, reliable, and efficient type of Low-Power Wide-Area (LPWA) Technology that was standardized by 3GPP and uses licensed spectrum.
		 * low power consumption
		 * low device cost
		 * low connectivity cost
		 * massive connections (tens of thousands of devices per base station)
		 * long range (about 5 km in dense urban areas and about 50 km in rural area)
		 * good signal penetration (can reach elevators inside buildings as well as basement and underground car parks)![[Pasted image 20231123133221.png]]

* As per June 2018, Sigfox has the lowest cost radio modules (<$5, compared to ~$10 for LoRa and $12 for NB-IOT).


# Routing in IoT

## Why Routing
* what is routing?
	* Low power wireless links can be too short to reach destination in one hop
	* Need to traverse multiple links to reach destination![[Pasted image 20231123134109.png]]
	* Routing = selecting the (best) path for network traffic from the source to its destination

	* Lots of criteria (“metrics”) to decide what is the best path:
		* Delivery delay
		* Link load
		* Router load

	* In WSN we have some more metrics:
		* energy consumption 
		* Battery level of a node
		* loss probability 

* Traditional Routing
	* A routing protocol sets up a routing table in routers![[Pasted image 20231123134316.png]]
	* A node makes a local choice depending on global topology
	* What if a node cannot know the global topology?

### Zigbee
* As we said, Zigbee defines Network layer & Application layer framework on top of 802.15.4.![[Pasted image 20231123134431.png]]

#### Network Layer Overview
* When considering the network layer / Zigbee:
	* Three kinds of devices: Coordinator (unique in the network), Router, End device
	* Three kinds of networks: Star, Tree, Mesh network![[Pasted image 20231123134522.png]]
	* P.S.: RFD must be an end device 

## Tree routing 
* In ZigBee, network addresses are assigned to devices by a distributed address assignment scheme
* ZigBee coordinator defines three network parameters
	* the maximum number of children (C$_m$) of a ZigBee router
	* the maximum number of child routers (R$_m$) of a parent node
	* the depth of the network (L$_m$)
* A parent device utilizes C$_m$, R$_m$, and L$_m$ to compute a parameter called C$_{skip}$
	* which is used to compute the size of its children’s address pools![[Pasted image 20231123134800.png]]

* If a parent node at depth d has an address A$_{parent}$,
	* the $n$'th child router is assigned to address: A$_{parent}$+(n-1)×C$_{skip}$(d)+1
	* $n$'th child end device is assigned to address A$_{parent}$+R$_m$ ×C$_{skip}$(d)+n![[Pasted image 20231123135424.png]]

### routing protocols
* in a star network
	* there is no routing

* In a tree network
	* Tree routing: utilize the address assignment to obtain the routing paths

* In a mesh network, there are 2 options:
	* Tree routing
	* AODV

* When a device receives a packet, checks if the destination is itself or one of its child devices
	* If so, accept the packet or forward it to a child
	* Otherwise, relay it along the tree                     ![[Pasted image 20231123140603.png]]
	* example 
		* 38 -> 45
		* 38 -> 92


## Direct diffusion
![[Pasted image 20231123140716.png]]
![[Pasted image 20231123140731.png]]
![[Pasted image 20231123140750.png]]![[Pasted image 20231123140806.png]]
## Dynamic source routing

## Ad Hoc On-Demand Distance Vector Routing

