* The big question is 
	* What do we agree on?
	* And when do we agree on what we agree on?

# Impossibility 
## Reliable multicast
* No failures, Easy
	1. B-multicast to everyone
	2. Wait till $N$ messages are received 
	3. Decide (e.g. minimum, majority,...)

* Failures?
	* Mechanism for failures detection
		* difficult/impossible for async systems 
			* dead or slow?
	* Mechanism for failure handling

## The two armies problem 
* Attack at 6h00
	* captain said "attack at 7h00". why not
* which protocol works

how do we know which is a traitor 
![[Pasted image 20231012125711.png]]
* L2 does not know if L1 or C lied about the hour

## The impossibility of Consensus (in async)
* Informally 
	* Communication can be "blocked" indefinitely!
* Reliable TO Multicast is also impossible in Async systems
	* same problem 

# System model
Lets assume a sync system
with reliable communication 
the processes can (faulty models) 
	crashes
	byzantine 
		arbitrary 
		Evil
if we signed messages 
	then we can see if the wrong messages comes from fx C or L1


# Requirements
![[Pasted image 20231012135705.png]]
* **Termination**: Eventually a correct process sets its decision variable di
* **Agreement**: The decision values of all correct processes are the same
* **Integrity**: if all correct processes propose the same value, then any correct process in the decided state decide on the value
* other "integrities" were proposed such as:
	* **weak integrity**: The agreed value must one proposed by a correct process


# Consensus Algorithms
## Synchronous consensus Algorithm 
* Some systems work in rounds
* Most things are not truly async
	* "Indefinitly" rarely happens

* goal 
	* f-crash-resilient synchronous consensus algorithm
* **f-resilient**
	* The algorithm is f-resilient is f processes may fail ![[Pasted image 20231012131626.png]]

* **Theorem**
	* Any optimal f-resilient consensus-algorithm requires f + 1 rounds
![[Pasted image 20231012132924.png]]


# Byzantine
* Byzantine Error
	* What is processes do not crash-fail but interact unpredictably 

* single event upset: A flipped bit
* single event latchup: Hardware error![[Pasted image 20231012133102.png]]![[Pasted image 20231012133129.png]]


* not only a space issue
	* "error-correcting code memory" ECC
	* bitflip on planes
	* nuclear power plants ...

### consensus
* Requirements 
	* **Byzantine Integrity**: if all non-faulty processes start with the same value, then all non-faulty processes decide on that value
		* this time the faults comprise sending "wrong" messages 

* goal
	* f-byzantine-resilient synchronous consensus algorithm 

* bad news
	* impossible for $f \leq \frac{n}{3}$

* good news 
	* possible otherwise 

### non-consensus 
![[Pasted image 20231012133705.png]]
![[Pasted image 20231012133727.png]]

### Three Equivalent Problems 
* Consensus
	* each process pi proposes a value vi
	* **termination**: Eventually each correct process sets its decision variable
	* **Agreement**: The decision variable of all correct processes are the same
	* **Integrity**: If the correct processes all proposed the same value, then any correct process in the decided state has chosen that value.

![[Pasted image 20231012135547.png]]
![[Pasted image 20231012135608.png]]
![[Pasted image 20231012135617.png]]

* byzantine generals algorithm (f=1)![[Pasted image 20231012135640.png]]![[Pasted image 20231012135733.png]]

## King Algorithm 
* Phase-King Algorithm                                 ![[Pasted image 20231012135802.png]]
* proof: ![[Pasted image 20231012140015.png]]

* analysis                                                                ![[Pasted image 20231012141215.png]]

![[Pasted image 20231012141248.png]]


# Fixing the async problem 
* I want to believe!
	* ... that there is a practical solution
* Be random
	* If we allow randomness is out algorithm we can have solution to byzantine generals problem in async setting
## Paxos 
* A family of algorithms by L. Lamport
	* No coordinator 
	* Async-systems
	* Nodes may crash and recover
		* ok with up to n/2 failures
	* once a single process decides, all will eventually decide the same

* Big problem!
	* no guaranteed termination
	* ... but terminates in "reasonable environments"

Watch Video https://youtu.be/d7nAGI_NZPk

RAFT Algorithm See https://www.usenix.org/conference/atc14/technical-sessions/presentation/ongaro