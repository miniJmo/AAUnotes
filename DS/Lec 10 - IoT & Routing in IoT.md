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

* EEE 802.15.4 MAC Overview
	* Optional Superframe Structure![[Pasted image 20231123131533.png]]


# Routing in IoT

## Why Routing

## Tree routing 

## Direct diffusion

## Dynamic source routing

## Ad Hoc On-Demand Distance Vector Routing

