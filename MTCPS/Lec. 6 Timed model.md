Like asynchronous model for communication of information 
can rely on global time for coordination 

example of a timed model:![[Pasted image 20230608151628.png]]

* clock variables: 
	* tests and updates in mode-switches like other variables
	* new feature: During a timed transition of duration $\delta$, the value of a clock variable increases by an amount equal to $\delta$

* Timing constraint: Setting x to 0 for "**off -> dim**" and guard **x<=1** for "**dim -> bright**" specifies that timing of these two transitions is <=1 apart

* clock invariant:
	* The constriant "y<=2"associated with the mode Full is called the clock invariant![[Pasted image 20230608154132.png]]
	* A timed transition of duration $\delta$ is allowed only when the clock invariant remains true during the entire duration
		* Timed transition (Full, x, y=0.8) – 0.7 -> (Full, x, y=1.5) allowed
		* Timed transition (Full, x, y=0.8) – 1.4 -> (Full, x, y=2.2) disallowed
	* Clock invariants useful to limit how long a process stays in a mode

## Timed Process 
* A Timed Process TP consists of 
	* An asynchronous process P, where some of the state variables can be of type clock
	* A clock invariant CI which is a boolean expression over the clock variables of P
* Define inputs, outputs, states, initial states, internal actions, input actions, output actions exactly the same as the asynchronous model
* Timed actions: Given a state s and real-valued time $\delta > 0, s-\delta \rightarrow s+\delta$ is a transition of duration $\delta$ if the state s+t satisfies the expression CI for all values of t in the interval \[0, $\delta$\] 
	* for a state s and time $\delta$,$s+\delta$ is another state which assigns the value $s(x)+ \delta$ to every clock variable x, and s(y) to every variable y of type other than clock
	* If clock-invariant is a convex constraint then it is sufficient to check that the end-states a and $s+\delta$ satisfy CI


## Mutual Exclusion problem
![[Pasted image 20230608164819.png]]
* Safety Requirement: Both processes should not be in critical section simultaneously (can be formalized using invariants)
* Absence of deadlocks: If a process is trying to enter, then some process should be able to enter

Example:![[Pasted image 20230608165151.png]]
* When a process wants to enter critical section, it reads the shared variable Turn
* If Turn != 0 then try again (goto step 1)
* If Turn = 0 then set Turn to your ID
* Proceeding directly to critical section is a problem (since the other process may also have concurrently read Turn to be 0, and updating Turn to its ID)
* Solution: Delay and wait till you are sure that concurrent writes are finished 
* Read Turn again: if Turn equals your own id then proceed to critical section, if not goto step 1 and try again
* When done with critical section, set Turn back to 0

### Fisher's protocol
![[Pasted image 20230608170830.png]]
* Assuming $\Delta_2 > \Delta_1$, the algorithm satisfies:
	* Mutual exclusion: Two processes cannot be in critical section simultaneously 
	* Deadlock freedom: If a process want to enter critical section then some process will enter critical section
* Protocol works for arbitrarily many processes 
	* Note: In the asynchronous model, mutual exclusion protocol for N processes is lot more complex than Peterson's algorithm
* Does the protocol satisfy the stronger property of starvation freedom: If process $P_i$ wants to enter critical section then it eventually will?
* If $\Delta_2 <= \Delta_1$ then does mutual exclusion hold? does deadlock freedom hold?


## Timing analysis
![[Pasted image 20230608181629.png]]
* How to adapt algorithms for searching through the state-space of a model in presence of clock variables and timing constraints?
* Application: Formal analysis of timing-based coordination and communication protocols, and many other systems...
* Must handle the space of clock valuations symbolically!
* Popular model checker: Uppaal

![[Pasted image 20230608182037.png]]
* timed Automata:
	* Motivation: When is exact analysis of timing constraints possible?
	* A timed process TP is a timed automation if for every clock variable x 
		* assignments to x in the description of TP are of the form x:=0
		* An atomic expression involving x in the description of TP (in clock-invariants or in guards) must of the form "x~k" where k is a constant and ~ is a comparison operation (=,<=,<,>,>=)
	* In such model, one can express constant lower and upper bounds on timing delays
		* closed under parallel composition: If TP1 and TP2 are timed automata then TP1 | TP2 is also timed automaton
	* Finite-state timed automation: A timed automaton where all variables other than clock variables have finite types (boolean, enumerated)
		* state-space is still infinite due to clock variables, but verification is solvable exactly.

### example 
![[Pasted image 20230608182925.png]]
![[Pasted image 20230608182934.png]]
![[Pasted image 20230608182942.png]]
![[Pasted image 20230608182952.png]]
![[Pasted image 20230608183001.png]]![[Pasted image 20230608183010.png]]![[Pasted image 20230608183023.png]]
![[Pasted image 20230608183035.png]]
