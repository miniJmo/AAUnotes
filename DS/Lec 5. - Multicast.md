* what is multicast?
	* A **multicast** is **one-to-many** communication between a single process and a **specific group** of processes such that **all members of the group receive the message**
	
	 * *Big Question*: How do we guarantee that everyone gets the same information? And what do we mean by **same** ?

* We assume closed groups, and 
* We assume static groups, 
* Not discussing multiple groups. 
	* Good news : All algorithms shown work both in sync and async networks

# IP Multicast
* Use internet Group Management Protocol (IGMP)
* Get IP group
	* IPv4: 224.0.0.0 - 239.255.255.255 (-224.0.0.255 for permanent)
	* IPv6: FF00::/8

* Build on UDP over IP

* it is not easy to support multicast (used to be, when talking about routers)
	* still problem with firewalls / NAT

![[Pasted image 20231005125106.png]]

* with no hardware support. have to send to all the other computers individually ![[Pasted image 20231005125236.png]]
* with support it makes a distribute tree![[Pasted image 20231005125212.png]]

* Problems 
	* UDP has no guarantees
		* there is no handshake, so there is no re-transmission
			* no reception garuanteed
			* one attempt only
		* No ordering 
			* messages are delivered in arbitrary order![[Pasted image 20231005125543.png]]
			* losing messages are also bad ![[Pasted image 20231005125619.png]]

# Requirements
* assume
	* perfect communication
		* Reliable 1:1 communication 
		* sender might crash
		* no order

* Guarantees 
	* If a message is sent, it is **delivered** exactly once
	* messages are eventually **delivered** to non-crashed processes
![[Pasted image 20231005130048.png]]



# basic multicast
* Delivery![[Pasted image 20231005130228.png]]
* Basic multicast ![[Pasted image 20231005130247.png]]
* sender can fail
* reliable send = ACK implosion 

# reliable multicast
* Properties 
	* Integrity
		* Messages are delivered at most once
	* Validity
		* A process delivers to itself (or crashes)
	* Agreement
		* All correct processes deliver, or no correct process deliver
![[Pasted image 20231005131225.png]]

* Integrity 
	* yes
* Validity
	* yes
* agreement
	* yes
* 1 muolticast = $O(N^2)$ messages in the network

## Over IP
![[Pasted image 20231005131655.png]]
![[Pasted image 20231005131704.png]]
![[Pasted image 20231005131716.png]]

* Integrity 
	* yes (IP also does checksum)
* Validity
	* Yes
* Agreement
	* ... not really

* No drops, good orderign = $O(N)$ messages
	* ... how many NACK’s can we send for one message?
	* ... when to send NACK's?
	* ... lot of small NACK/Resend?





# ordered multicast
![[Pasted image 20231005133126.png]]

* **mIstede total koncentrationen** luften er lort i fib 15

* Tag noter til resten senere...


## FIFO multicast

## totally ordered multicast

## Causally ordered multicast