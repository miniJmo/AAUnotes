* recap: In a synchronous model, all components execute in a sequence of logical rounds in lock-step

* Asynchronous model: Speed at which different components execute are independent (or unknown)
	* Processes in a distributed system
	* Threads in a typical operating system
* Key design challenge: how to achieve coordination?

### Example:
![[Pasted image 20230608125453.png]]
* Input task $A_i$  for processing of inputs: code: x := in 
* Output task $A_0$ for producing outputs: 
	* guard: x != null; code: out := x; x := null

* execution model: In one step, only a single task is executed 
	* Processing of inputs (by input tasks) is decoupled from production of outputs (by output tasks)
* A task can be executed if it is enabled, i.e., its guard condition holds 
	* If multiple tasks are enabled, only one of them is executed
* sample execution: ![[Pasted image 20230608130137.png]]

## Asynchronous composition 
Definition:
* Given asynchronous processes P1 and P2, how to define P1 | P2?

* Note: In each step of execution, only one task is executed 
	* Concepts such as await-dependencies are not relevant 

* Sample case ()
	* If y is an output channel of P1 and input channel of P2, and
	* A1 is an output task of P1 for y with code: Guard1 -> Update1, and 
	* A2 is an input task of P2 for y with code: Guard2 -> Update2, then
	* Composition has an output task for y with code: 
		* (Guard1&Guard2) -> Update1; Update2


## Atomic registers
![[Pasted image 20230608135131.png]]
* By definition of our asynchronous model, each step above is either internal to P1 or P2, or involves exactly one synchronisation: either read or write one shared variable by of the processes
* Atomic register: Basic primitives are read and write 
	* To "increment" such a register, a process first needs to read and then write back the incremented value
	* But these two are separate steps, and the register value can be changed in between by another process


data race: Concurrent accesses to a shared object where the result depends on the order of execution (This should be avoided!)


## Mutual exclusion problem
![[Pasted image 20230608142014.png]]
* critical section: Part of code that an asynchronous process should execute without interference from others
	* can include code to update shared objects/database
* Mutual exclusion problem: Design code to be executed before entering critical section by each process
	* Coordination using shared atomic registers 
	* There is no assumption about how long a process stays in critical section 
	* A process may want to enter the critical section repeatedly 

* Safety requirement: Both processes should NOT be in critical section simultaneously 
* Liveness requirement: Starvation freedom: If a process is trying to enter, then eventually it should be able to enter


Fairness:
* uncoditional fairness: An inifite execution is unconditionally fair to a task A if task A is executed repeatedly during this execution 
* weak fairness: An infinite execution is weakly fair to a task A if, repeatedly, task A is either executed  or disabled 
	* In other words: if A is almost always\* enabled, then A is infinitely often taken \*only finitely many exceptions
* strong fairness: An infinite execution is strongly fair to a task A if A is either repeatedly executed or almost always disabled
	* In other words: if A is infinitely often enabled, then A is infinitely often taken
