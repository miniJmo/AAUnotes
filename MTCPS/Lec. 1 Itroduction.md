![[Pasted image 20230607111848.png]]


## Interfaces for components
Cruise control:
* Drivers interacts with the system using 4 buttons
	* cruise: cruise control (on/off)
	* pause: to suspend/restart its operation
	* inc/dec: to increment or decrement desired speed![[Pasted image 20230607112453.png]]
	* But the cruise controller also need to know the current speed:![[Pasted image 20230607112931.png]]
	* lastly it also needs to send an output of force to the throttle and the current speed and desired speed to the display:![[Pasted image 20230607113851.png]]

Then it is possible to decompose the interface to this:![[Pasted image 20230607114038.png]]


## State machine
For the SetSpeed we need to design a state machine that controls that we are at the desired speed and that we ![[Pasted image 20230607114818.png]]


For the ControlSpeed we need som capturing requirements:
* requirements: Mathematically precise description of what a system is supposed to do. Writing requirements is key to ensuring reliability of systems
	* Requirement 1: Actual speed eventually converges to desired speed
	* Requirement 2: Speed of the car stays "stable"![[Pasted image 20230607130641.png]]
	* control theory: Mathematical techniques to compute force as a function of velocity and desired speed
	* We can use verification tools to check if a system model indeed works as expected, that is satisfies the requirements

Model-based design does not equal coding 
* Design using high-level block diagrams and state machines gets automatically compiled into low-level code ! Not only a model of the designed system, but also of its environment

### Formal verification 
![[Pasted image 20230607141119.png]]
Goal: 
* Establish that model satisfies requirements under all possible scenarios 
First challenge: 
* Need formal definitions of "model" and "requirements" to make the problem mathematically precise
Second challenge:
* Need verification techniques and tools


# Synchronous Model
Synchronous models have
* All components execute in a sequence of (logical) rounds in lock-step
* Example: Component blocks in a digital hardware circuit
	* clock drives all components in a synchronised manner
* Key idea: Design system using a synchronous round-based computation 
	* Benefit: design is simpler
	* Challenge: Ensure synchronous execution even if implementation platform is not single-chip hardware

#### Example:
![[Pasted image 20230607152715.png]]
* Input variable: *in* of type boolean 
* output variable: *out* of type boolean
* state variable: *x* of type boolean
* Initialisation of state variables: assignment *x := 0*
* In each round, in response to an input, produce output and update state by executing the update code: *out := x; x := in*

round-based execution (still the bool example):
* Initialise state to 0
* Repeatedly execute rounds. In each round:
	* choose a value for the input variable in
	* Execute the update code to produce output out and change status 
* sample execution:![[Pasted image 20230607161918.png]]

## Synchrony Hypothesis
* Assumption: 
	* Time needed to execute the update code is negligible compared to delay between successive input arrivals 
* logical abstraction:
	* Execution of update code takes no time
	* production of outputs and reception of inputs occurs at same time
* when multiple components are composed, all execute synchronously and simultaneously 
* implementation must ensure that this design-time assumption is valid 


## Synchronous Reactive Component (SRC)
Definition:
* Set I of typed input variables: gives set $Q_I$ of inputs 
* Set O of typed output variables: gives set $Q_O$ of outputs 
* Set S of typed state variables: gives set $Q_S$ of states 
* Initialisation code Init: defines set [Init] of initial states 
* Reaction description React: defines set [React] of reactions of the form s –i/o-> t, where s, t are states, i is an input, and o is an output


## Extended state machine (ESM)
![[Pasted image 20230607173537.png]]
* *Mode* is a state variable ranging over {on, off}
* Reaction corresponds to executing a *mode-switch*
* Example mode-switch: from on to off with
	* *guard*(press=1|x>=10) and *update* code x:=0

## Finite-state component 
Definition:
* A component is finite-state if all its variables range over finite types
	* Finite types: bool, enumerated types(on, off), int[-5,5]
	* Delay is finite-state, but Diffsquare is not![[Pasted image 20230607174238.png]]
	* Finite-state components are amenable to exact, algorithmic analysis


## Deterministic 
* A component is deterministic if it has a single initial state, and for every state s and input i, there is a unique state t and output o such that s-i/o->t is a reaction
* Deterministic: If same sequence of inputs supplied, same outputs observed (predictable, repeatable behaviour)


## Tasks
![[Pasted image 20230607181232.png]]
* A1 and A2 are tasks (atomic blocks of code)
	* each task specifies variables it reads and writes 
	* A1 reads x and writes out
* Task graph: Vertices are tasks and edges denote precedence 
	* A1 < A2 means that A1 should be executed before A2
	* Graph sould be acyclic![[Pasted image 20230607181635.png]]
	* Notation: A’ <+ A means that there is a path from task A’ to task A in the task graph using precedence edges (<+ denotes the “transitive closure” of the relation <)


