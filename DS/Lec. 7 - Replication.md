* Exam: 15-18 Jan
	* oral
	* 20 mins in total
	* 9 topics (from course)
		* 10 mins presentation
			* can make slides or other material
		* 10 mins question 


# Goal
* High Tolerance 
	* Transparent to user
	* Tolerates node/network failures 
* high availability 
	* service is rarely interrupted 
* Performance 
	* Limits of vertical scaling
	* Overcome geographic/network limits 
![[Pasted image 20231024124344.png]]

*Important* note:
* caching is also replication
	* local browser cache
	* prefetching for netflix
	* DNS registry  

# CAP Theorem 
* CAP
	* Consistency
		* bank account is the same, regardless of server
	* Availability 
		* bank account is always accessible, no delays
	* Partition tolerance 
		* Loss of connection will not disturb bank-service

* **Theorem**
	* It is **impossible** for a distributed computer system to simultaneously provide **Consistency**, **Availability** and **Partition Tolerance**. A distributed system *can satisfy any two* of these guarantees at the same time, but **not all three**.

## The choice
![[Pasted image 20231024125607.png]]
* examples![[Pasted image 20231024130242.png]]

# Assumption 
* Assumptions 
	* Async system
	* Reliable communication
	* crash-fail
	* atmoc operations
	* object are "state machines"
		* no random
		* no timer
		* no external events

* Notation
	* o.m(v) = apply modifier m to object o with value v myAccount.deposit(1000)![[Pasted image 20231024130509.png]]

* Requirements 
	* transparent for user
	* consistent in replicated objects

	* Ideal 
		* Indistinguishable from single copy behaviour


# Replication techniques
* see example in slides for operations
# Fault Tolerance 
![[Pasted image 20231024131406.png]]![[Pasted image 20231024131419.png]]

* see example in slides for inconsistency

* desired Temporal consistencies 
	* if I write a value, I will see that (or a newer value) on a subsequent read
	* if I read twice, the value returned on the second read is at least as new as from the first read
	* if data is related (questions and answers), I expect this to be reflected in a consistent manner
		* ... no constraints on unrelated data!

* Linearizability (Lamport)![[Pasted image 20231024131948.png]]![[Pasted image 20231024132156.png]]

# Availability 

## Gossip Architecture 



