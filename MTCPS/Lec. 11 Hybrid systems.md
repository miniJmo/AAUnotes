* Generalisation of timed processes
* During timed transitions, evolution of state/output variables specified using differential equations as in dynamic systems


Take a self-regulating switching thermostat: ![[Pasted image 20230609212204.png]]
* state machine with two modes plus state variable T to model temperature with type cont
* T can be tested and updated during mode-switches
* T changes continuously during timed transitions given by differential equations 
* Invariants (as in timed model) constrain how long can a transition be

* Execution
	* initial state = (off, $T_0$) with $T_0$ in the interval [60,70]
	* During a timed transition, T decreases continuously: $T(t) = T_0 -k_2 t$ 
	* Mode-switch to on is enabled when $T<= 62$, and must happen before T reaches 60
	* As time elapses in mode on, T increases according to $T(t)=70-(70-T^*)e^{-k1(t-t^*)}$, $t^*, T^*$: time and temperature upon entry to mode on
	* Mode-switch to off is enabled when $T>=68$, and must happen before T reaches 70
	* looks like this:        
		* ![[Pasted image 20230609214408.png]]


Bouncing ball modeling:
* Ball dropped from an initial height $h_0$ with an initial velocity $v_0$
* Velocity changes according to the differential equation $dv/dt=-g$
* when the ball hits the ground, that is, when height $h=0$, velocity changes discretely: $v:=-av$, where $0<a<1$ is dampening constant
* modled as a hybrid system: mix of discrete and continuous behaviours 
	* hybrid process of bouncing ball: ![[Pasted image 20230609215433.png]]
	* execution: ![[Pasted image 20230609215452.png]]

## definition of a hybrid process
the syntax:
* A hybrid process HP consist of
	* An asynchronous process P, where some of the state variables can be type cont
	* A continuous-time invariant CI which is a boolean expression over the state variables of P
	* For every output variable y of type cont, a Libschitz-continuous real-valued expression that gives the value of y as a function of state variables and continuous input variables
	* For every state variable x of type cont, a Libschitz-continuous real-valued expression that gives the rate of change of x as a function of state variables and continuous input variables

The semantics:
* Define inputs, outputs, states, initial states, internal actions, input actions, output actions exactly the same as the asynchronous model
* Timed actions: Given a state s and real-valued time $\delta > 0$ and a continuous input signal $u(t)$ that gives value for continuous inputs over time interval \[0,$\delta$\], the corresponding state/output signal over \[0,$\delta$\] is uniquely defined so that
	* Initial state $s(0)$ equals $s$
	* Discrete (i.e. non-cont) state variables stay unchanged
	* for each continuous output variable y, the value $y(t)$ satisfies the corresponding algebraic equation 
	* for each continuous state variable x, the derivative $dx(t)/dt$ of the signal satisfies the corresponding differential equation
	* At all times t in \[0,$\delta$\], the signal value $s(t)$ satisfies the invariant constraint CI


## Execution of hybrid processes
starting from an initial state either a discrete step (as in input, or output or timed interval action) or a timed step (this is needed to solve system of differential equations)
example:
* (off, 66) –2.5-> (off, 61) -> (on, 61) –3.7->(on,69.02) -> (off, 69.02) –4.4-> (off, 60.22) -> (on, 60.22) –7.6-> (on, 69.9) -> (off, 69.9) –4.1->(off, 61.7) -> (on, 61.7) …![[Pasted image 20230609221559.png]]
* concepts based on transition systems such as reachable states, safety and liveness requirements, all apply to hybrid systems


## block diagrams
* Component processes can now be hybrid processes
	* Need to define Instantiation, Composition, output hiding
* Channels connecting processes of two types
	* sender/receiver communication of values during discrete steps as in the asynchronous model
	* Continuously evolving signals during timed steps as in the model of continuous-time dynamical systems


## analysis of bouncing ball model
![[Pasted image 20230609215433.png]]
* the change in height during the first bounce: $h(t)=h_0 -gt^2/2$
* Time at which first bump occurs: $t_1 =\sqrt{2 h_0/g}$
* velocity just before first bump: $-\sqrt{2gh_0}=-v_1$
* velocity just after first bump: $v_2 = av_1$
* Evolution of height during the second bounce: $h(t)= v_2t-gt^2/2$
* Time between first and second bump: $t_2 = 2v_2/g$
* Velocity just before second jump: $-v_2$ and after: $v_3 = av_2$

what we can take from this is:
* velocity after k bumps = $a^kv_1$
* duration between k-th and following bump $a^kv_1/g$
* sum of all durations converges to some finite K
* Infinity many discrete actions in finte time (Zeno behaviour)
* An execution with infinitely many discrete actions describe behaviour only up to a certain time K and does not tell us the state of the system beyond K


## Zeno vs Non-zeno
An infinite execution is called Zeno if the infinite sum of all the durations is bounded by a constant, and non-zeno if the sum diverges.

* A state s of the process HP is called 
	* Zeno if every execution starting in state s is Zeno 
	* Non-Zeno if there exists some non-Zeno execution starting in s 
* A hybrid process HP is called non-Zeno if every reachable state of HP is non-Zeno

* Zeno system: Could end up in a state from which duration between successive steps must get smaller and smaller

Thermostat: Non-Zeno 
Bouncing ball: Zeno

examples:
* Zeno, every possible execution is Zeno ![[Pasted image 20230609224228.png]]

* Non-Zeno, some executions are Zeno and some are Non-Zeno![[Pasted image 20230609224311.png]]

* Zeno, system may end up in a state from which only Zeno executions are possible![[Pasted image 20230609224404.png]]


### Zeno Processes and Reachability 
How does Zeno processes influence analysis?
* recall: A state s is said to be reachable if there exists a finite execution starting in an initial state and ending in state s
* Safety: A property $\varphi$ is an invariant if all reachable states satisfy $\varphi$

Presence of a Zeno process in the system can stop time from advancing, and make states of other processes unreachable:![[Pasted image 20230609225653.png]]


Making the bouncy ball Non-Zeno:
* If the velocity is too small, stop modeling dynamics accurately 
* In this model, there is a lower bound on duration between successive bumps![[Pasted image 20230609225910.png]]


## Stability analysis
![[Pasted image 20230609230005.png]]
![[Pasted image 20230609230012.png]]

