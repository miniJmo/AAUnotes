* Controller (software) interacting with the physical world via sensors and actuators
	* Cruise controller regulating speed of a car, etc...

* Variables: Physical quantities evolving continuously over time
	* Temperature, pressure, velocity, etc...

* Governed by nature's laws
	* newton's law
	* thermodynamics
	* Maxwell's equations

* Continuous-time models using differential equations 

## Model-based Design Example
* what are the execution semantics 
	* Similar to synchronous model, but continuous-time instead of discrete-time

* water flow example: ![[Pasted image 20230609131718.png]]
	* Inflow of water $Q_{in}$ 
	* Outflow of water $Q_{out}$ 
* which gives us this model: ![[Pasted image 20230609131842.png]]
* all of type real
* no state variables
* Signal: assignment of values to variables as function of time $t$ 
* at each time $t$, value of output signal $Q_{net}(t)$ equals $Q_{in}(t)-Q_{out}(t)$ 
* Output as a function of inputs/state specified using algebraic equations (as opposed to assignments)

* Car model example:![[Pasted image 20230609132715.png]]
* which gives us this model![[Pasted image 20230609132840.png]]
* For state variable $v$, its rate of change $dv/dt$ is defined using an expression over input and state variables
* For each output variable, its value is defined using an expression over input and state variables.

* now with position variable x:![[Pasted image 20230609133310.png]]
* which gives us this model:![[Pasted image 20230609133333.png]]
	* remember that $a= dv/dt$ and $v=dx/dt$ 
	* we can rewrite $F-kv = md^2x/dt$ into the system above using state variables $x$ and $v$.

	* execution of car:
		* Input signal: function $F(t): real_{\geq 0} \rightarrow real$ that gives value of force as a function of time 
			* should be continuous or piecewise-continuous 
		* Given an initial state ($x_0,v_0$) and input signal $F(t)$, the execution of the system is defined by state-signals $x(t)$ and $v(t)$ (from $real_{\geq 0}$ to $real$) that satisfy the initial-value problem:
			* $x(0)=x_0;v(0)=v_0$
			* $dx(t)/dt=v(t)$
			* $dv(t)/dt=(F(t)-kv(t))/m$


## Calculus 
* $\frac{d}{dt}x(t)$ captures the rate of change of variable $x$ at time $t$, i.e. the slope
* $\frac{d}{dt}x(t)$ is defined as the limit of the difference: $\frac{d}{dt}x(t)=\lim_{h\rightarrow 0} \frac{x(t+h)-x(t)}{h}$ ![[Pasted image 20230609134949.png]]

* exact formulation: $\frac{d}{dt}x(t)=f(x(t))$ 
* Approximation: $\frac{x(t+h)-x(t)}{h} \approx f(x(t)) \Leftrightarrow x(t+h) \approx x(t)+h\cdot f(x(t))$![[Pasted image 20230609140851.png]]

* Euler method:
	* Input: $f,x_0,h,N$

	* $\tilde{x}_0 \leftarrow x_0$
	* for $i \in \{0,1,\dots,N\}$ do
		* print $\tilde{x}_i$
		* $\tilde{x}_{i+1} \leftarrow \tilde{x} + h \cdot f(\tilde{x}_i)$
	* end

 * Theorem:
	 * $\exists C > 0.\forall h > 0.\forall i \in \{0,1,\dots,N\}:$
	 * $|\tilde{x}_i - x_i| \leq C\cdot h$
	 * So, the global truncation error is proportional to $h$.

Example of Euler method:![[Pasted image 20230609153922.png]]
![[Pasted image 20230609153937.png]]

### Runge-Kutta
* the Euler method assumes that the rate of change is constant during the interval, and is only based on the state at the beginning of the interval
* This is often not the case for dynamic systems
* we could take the endpoint into account as well.
* Runge-Kutta methods are based on this idea

* Second-order Runge-Kutta method uses the following calculations:
	* $k_1 = f(x(t))$ <- slope at beginning of interval
	* $k_2 = f(\tilde{x}_i+h\cdot k_1)$ <- Estimated slope at end of interval
	* $\tilde{x}_{i+1} = \tilde{x}_i +h \cdot (k_1 + k_2)/2$ <- Euler method, but now average slope

* Most commonly used method is the fourth-order Runge-Kutta method
	* It takes four slopes into account: start, two midpoints and endpoint 

	* $\tilde{x}_{i+1} = \tilde{x}_i + h(k_1+2k_2+2k_3+k_4)/6$
		* see book for expression of $k_1,k_2,k_3,k_4$ 

	* Theorem:
		* $\exists C > 0.\forall h > 0.\forall i \in \{0,1,\dots ,N\}:$
			* $|\tilde{x}_i - x_i| \leq C \cdot h^4$
		* note that for $0<h<1:h^4 \ll h$ 
		* So, the fourth-order Runge-Kutta method is more efficient than Euler method


### car example plotted in
![[Pasted image 20230609163035.png]]


## Continuous-Time Component 
* Set $I$ of real-valued input variables 
* Set $O$ of real-valued output variables
* Set $S$ of real-valued state variables
* Initialisation $Init$ specifying Set \[$Init$\] of initial states
* For each output var $y$, a real-valued expression $h_y$ over $I\cup S$ 
* For each state variable $x$, a real-valued expression $f_x$ over $I \cup S$
* Given an input-signal $I(t): real_{>= 0} \rightarrow real^{|I|}$, an execution consists of a *differentiable* state signal $S(t)$ and output signal $O(t)$ such that 
	* $S(0)$ is in $[Init]$ 
	* For each output var $y$ and time $t, y(t) = hy(I(t),S(t))$
	* For each state var $x, (d/dt) (x(t)) = fx(I(t),S(t))$


### Existence and uniqueness
* Given an input signal $I(t)$, when are we guaranteed that the system has at least one execution? Exactly one execution? 
* The input signal should be continuous (or at least piecewise continuous), but also depends on right-hand-sides of equations defining state and output dynamics
* Related to classical theory of ODEs (Ordinary Differential Equations)
* Consider the initial value problem
	* $dx/dt= f(x); x(0) = x_0, x$ is $k$-dimensional signal
* When does there exist a unique differentiable function $x(t)$ as a solution?

#### Existence 
![[Pasted image 20230609165500.png]]

#### Uniqueness
![[Pasted image 20230609165527.png]]


## Lipschitz Continuous Component 
* A continuous-time component has Lipschitz-continuous dynamics if 
	* Each expression $h_y$ corresponding to output variable $y$ is a Lipschitz-continuous function of $I \cup S$ 
	* Each expression $f_x$ corresponding to state variable $x$ is a Lipschitz-continuous function of $I \cup S$ 
* If we supply a Lipschitz continuous component with a continuous input signal $I(t)$, then it has a unique response signals $S(t)$ and $O(t)$, both of which are continuous
* Note: Continuity of output signals means these can be fed to other components in a block diagram 
* Henceforth, we will assume all components are Lipschitz-continuous 

## CtC Car2
* what if the car was driving up a hill
	* then we have to take the angle into account![[Pasted image 20230609173228.png]]
	* The grade of the road, denoted $\theta$, models disturbance or an uncontrolled input![[Pasted image 20230609173407.png]]

## Pendulum model
![[Pasted image 20230609173853.png]]
* External torque applied by the motor at the pivot: $u$
* Dynamics captured by the second-order non-linear differential equation: $ml^2(\frac{d^2}{dt})\varphi = u-mgl \sin\varphi$

	* note that $\frac{d}{dt}\varphi = v$, so $\frac{d^2}{dt}\varphi = \frac{d}{dt}(\frac{d}{dt}\varphi)=\frac{d}{dt}v$ 
	* when rewriting $ml^2(\frac{d^2}{dt})\varphi = u-mgl \sin\varphi$
		* $ml^2\frac{d}{dt}\varphi = u-mgl \sin\varphi$
		* $\frac{d}{dt}v=\frac{u}{ml^2}-\frac{g}{l}\sin\varphi$![[Pasted image 20230609174653.png]]

### angular Displacement 
* External Torque = 0; Initial displacement = $\pi/4$
	* Oscillatory motion plotted by mathlab![[Pasted image 20230609174833.png]]
* Consider $dx/dt=f(x)$. An $x$ satisfying $0=f(x)$ is called equilibrium

### what is the equilibria of this pendulum 
* consider a closed (i.e. without inputs) continuous-time component $H$ 
	* if $H$ has inputs, then we can analyse equilibria by setting inputs to a fixed value
	* Assume state $x$ is $k$-dimensional, and dynamics is Lipschitz-continuous given by $dx/dt = f(x)$ 
* A state $x_e$ is called an equilibrium of $H$ if $f(x_e)=0$
* If initial state of $H$ equals an equilibrium $x_e$, then the system stays in this state at all times

* Dynamics when external torque is 0: $d\varphi = v; dv = -(\frac{g}{l})\sin \varphi$
* Equilibrium states: $v=0; \sin \varphi = 0$
	* Equilibrium state 1: $v = 0; \varphi = 0;$ Pendulum is vertically downwards
	* Equilibrium state 2: $v = 0; \varphi = -\pi;$ Pendulum is vertically upwards


## Stability of Dynamic systems
* Key correctness requirements for dynamical systems: stability 
	* small perturbations in the input values should not cause disproportionately large changes in the outputs
* For cruise controller, correctness requirements:
	* Safety: Speed should always be within certain threshold values
	* Liveness: Actual speed should eventually get close to desired speed
	* Stability: If grade of the road changes, speed should change only slowly 

* classical mathematical formalisation of stability:
	* Lyapunov stability of equilibria 


### Lyapunov Stability 
* Consider a closed continuous-time component H with Lipschitz-continuous dynamics 𝑑𝑥/𝑑𝑡 = 𝑓(𝑥) 
* Given an initial state 𝑠, let 𝒙[𝑠] denote the unique state response signal for the initial value problem 𝑥(0) = 𝑠 and 𝑑𝑥/𝑑𝑡 = 𝑓(𝑥)
* Consider an equilibrium state $s_e$: if initial state is $s_e$ then the response 𝒙\[$s_e$\] is a constant function of time, always equal to $s_e$
* Stability of an equilibrium: when the system is in an equilibrium state, if we perturb its state slightly
	* As time passes, will the state stay close to the equilibrium state ?
	* As time passes, will the system eventually return to the equilibrium state?

* Suppose the inital state $s$ is close to an equilibrium state $s_e$, does the state along the response signal $x[s]$ stay close to $s_e$?
	* if so, equilibrium $s_e$ is said to be stable
	* Formally, for every $\varepsilon >0$, there exists $\delta > 0$ such that for all states $s$ with $||s-s_e||<\delta$, for all times $t\geq 0, ||x[s] (t)-s_e|| < \varepsilon$ ![[Pasted image 20230609182415.png]]

* If in addition, the response signal $x[s]$ converges to the equilibrium state $s_e$, then the equilibrium is asymptotically stable
	* there exists $\delta > 0$ such that for all states $s$ if $||s-s_e|| < \delta$ then the limit $\lim_{t\to\infty} x[s] (t)$ exists and equals $s_e$
	* Note: This is a stronger condition than stable![[Pasted image 20230609183042.png]]
* this makes the pendulum stable but not asymptotically stable for equilibrium state 1, and unstable for state 2


## input-output stability 
* A contionuous-time component $H$ maps input signal $I(t)$ to output signal $O(t)$
* Input-output stability: If we change the input signal slightly, the output signal should change only slightly![[Pasted image 20230609183549.png]]![[Pasted image 20230609183613.png]]
![[Pasted image 20230609183722.png]]




