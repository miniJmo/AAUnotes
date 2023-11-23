## Zones / Difference Bounded Matrices
zones:![[Pasted image 20230608190250.png]]
Zone operations:![[Pasted image 20230608190304.png]]

Data structures for zones:
* Difference Bounded Matrices (DBMs)
* Minimal constraint Form
* Clock difference diagrams 

## Real Time Scheduling 
* why scheduling?
	* if you only have one cpu
		* only one task can be executed at a time 
	* scheduling: which task should execute a given point in time

Terminology:
* ![[Pasted image 20230608193449.png]]


## Cyclic Executives
![[Pasted image 20230608195728.png]]

How to determine minor and major cycles 
minor:
* Task periods must be integer multiples of minor cycle period 
* Minor cycle period should be as large as possible $T_m = gcd(T_1,\dots,T_n)$ (gcd greatest common divisor) 
Major:
* Integer multiple of all task periods
* Major cycle period should be as small as possible  $T_M = lcm(T_1,\dots,T_n)$ (lcm least common multiple) 

![[Pasted image 20230608200614.png]]
![[Pasted image 20230608200626.png]]

## Task based scheduling 
Architecture:
* ![[Pasted image 20230608200807.png]]

Fixed Priority Scheduling (FPS)
* Definition: 
	* Each process had a fixed, static, priority assigned before run-time 
	* Priority determines execution order
* FPS is the most widely used approach 
* priority $\neq$ Importance 
	* In RTSs the "priority" of a process is derived from its temporal requirements, not its importance to the correct functioning of the system or its integrity 

Earliest Deadline first (EDF)
* Definition:
	* Execution order is determined by the absolute deadlines
	* The next process to run is the one with the shortest (nearest) deadline
	* Absolute deadlines must be computed at run-time (dynamic scheduling)

* why (not) EDF
	* Optimal (FPS can be made into EDF)
	* less supported
	* Harder to implement 

* Preemption vs non-preemption![[Pasted image 20230608203406.png]]

assign Priorities (FPS):
* Rate Monotonic Priority Assignment
* Each process is assigned a (unique) priority based on its period: $T_i<T_j \Rightarrow P_i>P_j$ 
* Note: priority 1 is the lowest priority ![[Pasted image 20230608203716.png]]
* Theorem: Any process set scheduled with a fixed-priority assignment scheme can also be scheduled with a rate monotonic assignment scheme

## Utility Based Analysis
Assume rate monotonic priority assignment 
Sufficient scheduling test for D = T task sets:![[Pasted image 20230608205325.png]]
![[Pasted image 20230608205351.png]]
example:![[Pasted image 20230608205408.png]]

### Utility test for FPS
![[Pasted image 20230608205608.png]]
EDF:
![[Pasted image 20230608205623.png]]

### Summary
pros and cons:
* Easy to perform 
* "Binary" answer
* Low utilisation (for FPS)

FPS vs EDF:
* FPS is easier to implement as priorities are static 
* EDF requires more complex run-time system with higher overhead
* Easier to incorporate other factors into a priority than into a deadline 
* During overload situations
	* FPS is more predicable: low priority processes miss their deadlines first
	* EDF is unpredicable: domino effect may occur: large number of processes miss deadlines

## Response Time Analysis
calculating the slowest Response:
* Calculate i's worst case response time: $R_i = C_i + I$. where $I$ is the interference from higher priority tasks
* check (trivially) if deadline is met $R_i\leq D_i$ ![[Pasted image 20230608210918.png]]

* Calculating $I$
	* During $R_i$ task j (with $P_j > P_i$) is released $\lceil \frac{R_i}{T_j}\rceil$ number of times.
	* Total interference by task j is given by: $$\lceil \frac{R_i}{T_j}\rceil C_j$$

Response-Time equation:
* worst case response time $$R_i = C_i + \sum_{j\in hp(i)} \lceil \frac{R_i}{T_j}\rceil C_j$$
* where hp(i) is the set of tasks with priority higher than task i ![[Pasted image 20230608211633.png]]![[Pasted image 20230608211714.png]]

