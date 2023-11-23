* A safety requirement states that a system always stays within "good" states (nothing bad ever happens)
	* like cruise controller the desired speed stays between bounds

* A liveness requirement states that a system eventually gets to a goal state
	* like actual speed getting to the desired speed in a cruise controller 

## Transition system
![[Pasted image 20230607215439.png]]

* Syntax: a transition system T = (S, Init, Trans) consists of 
	* a set S of typed state variables
	* Initialisation Init for state variables
	* Transition description Trans to update state variables

A state s of a transition system is reachable if there is an execution starting in an initial state and ending in the state s

Property ϕ is an invariant of T if every reachable state satisfies ϕ
* Invariants are safety properties 
* Express desired safety requirement as property ϕ of state variables 
	* If ϕ is an invariant, then the system is safe 
	* If ϕ is not an invariant, then some state satisfying ~ϕ is reachable (and an execution leading to such a state is a counterexample)

# Dynamic vs static analysis
* Dynamic analysis
	* Execute the system multiple times with different inputs
	* check if every execution meets the desired requirements
* Static analysis
	* Analyse the source code or the model for possible bugs 
* trade-offs
	* Dynamic analysis is incomplete, but accurate 
	* static analysis can catch design bugs early
	* static analysis is often not scalable (solution: analyse approximate versions, which can lead to false warnings)

Theorem:
* If $\varphi$ is an inductive variant, then all reachable states of T must satisfy $\varphi$, and thus, $\varphi$ is an invariant 

* Inductive strengthening 
	* property $\Psi$ implies property $\varphi$  
![[Pasted image 20230608114434.png]]

Say we want to prove that ϕ is an invariant If we can prove that ϕ is an inductive invariant, the theorem implies that ϕ is an invariant 
* However, the converse of the theorem does generally not hold 
	* Not every invariant is inductive, so ϕ may not be inductive 
* Good news: If ϕ is indeed an invariant, there is always an inductive strengthening ψ of ϕ that is an inductive invariant – why? 
	* Pick ψ as “set of reachable states” (which satisfies ϕ by definition) 
* Bad news: The set of reachable states (ψ) cannot generally be computed


# Safety monitor
* A monitor observes the input/output of a system and enters an error state if undesirable behaviour is detected 
* A monitor M is typically specified as extended state machine
	* The input variables of M are the input/output variables of the system being monitored
	* An output of M cannot be an input to the system (monitor is not supposed to influence what the system does)
	* A subset F of the modes of the state machine is accepting ("fail")
* Undesirable behaviour: A execution that leads monitor state to F
* safety verification: check whether (monitor.mode not in F) is an invariant of system C || M 
