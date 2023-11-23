* mutex algorithm; what is a good mutex?
	* must be safe, not more than process can access
	* but must give access 


# System Model
* computation is quick
* communication is slow
	* aka. bottleneck 
	* less communication is faster 

![[Pasted image 20230928124956.png]]

* sync does not allow reordering so we don't end out in this![[Pasted image 20230928125241.png]]

* but async have underlying protocols that allows for re-transmission, if a process crashes (dies)

![[Pasted image 20230928125555.png]]


# Mutex Algorithm 
## Centralised Algorithm
* Assume one external coordinator 
	* Coordinator has ordered queue 
* Ask coordinator for access

* see code example

* Requirements
	* Safe: yes
	* Liveness: yes
	* Ordering: no

* Properties
	* Client Delay
		* Entry: 2 (request + grant)
		* Exit: 1
	* sync Delay
		* 2 (Release + grant)
	* Bandwidth 
		* Entry: 2 (Request + grant)
		* Exit: 1 (Release)

* Fault Tolerance 
	* Deadlock if Coordinator fails 
	* Deadlock if mutex-holder fails 
	* Deadlock if a process in the waiting list fails

## Token Ring Algorithm 
* send token around in a ring 
	* ordering of processes in a ring (pro. 2 talks to 1 & 3) (pro. n talks to n-1 & 0)
* Forward token to “next” if not using mutex
* Enter mutex if token is acquired

* Requirements 
	* safe: yes
	* liveness: yes
	* ordering: no (order by ring)

* Properties 
	* client delay
		* entry: n/2 avg. n-1 worst case
		* exit: 1
	* sync delay
		*  n/2 avg. n-1 worst case
	* bandwidth
		* entry: $\infty$ 
		* exit: 1

* fault tolerance
	* deadlock if any process fails
	* can be recovered if crash can be detected reliably 

## Ricart and Agrawala's Algorithm 
* Order events
	* extension of shared priority queue 
* basic algorithm
	* request all for access
	* wait for all to grant

* Lamport clocks
	* Counter number of messages/events
	* annotate messages with clock 
	* increment local clock before send
	* "correct" local clock on receive, then increment when sending
		* max (A,B) + 1                           ![[Pasted image 20230928133216.png]]

* Requirements 
	* safe: yes
	* liveness: yes
	* ordering: yes
	
* Properties 
	* client delay
		* entry: 1 (multicast) + 1
		* exit: 1 (multicast) + 1
	* sync delay
		* 1
	* bandwidth
		* entry:
			* 1 + n - 1 (if hw multicast)
			* n - 1 + n - 1 (if no hw multicast)
		* exit: up to n - 1, included into entry 

* fault tolerance
	* deadlock if any process fails

## Maekawas Algorithm 
* only communicate with a subset ( Voting set V)
* pick V cleverly
* basic algorithm 
	* ask everybody in V for access
	* wait for all to grant

* voting set![[Pasted image 20230928135210.png]]

* this algorithm is prone to deadlock
	* solution
		* singhal algorithm, which is similar to consensus (lec. 6)

* Requirements
	* safe: yes
	* liveness: yes
	* ordering: yes

* properties 
	* client delay
		* entry: 2 (multicast)
		* exit: 1 (multicast)
	* sync delay
		* 2
	* bandwidth (with the heuristic and no hw multicast)
		* entry: $4 \sqrt n - 1$
		* exit: $2 \sqrt n -1$

* fault tolerance 
	* deadlock process in voting-set crashes.

## overview of mutex algorithms 
![[Pasted image 20230928140426.png]]


