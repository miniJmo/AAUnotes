Jakob Meyer Olsen 
20205341

## Exercise 1
### A
$(add,0)\rightarrow ^{(2,\bot)/(2)}(add,2)\rightarrow ^{(3,\top)/(3)}(mul,3)\rightarrow ^{(1,\top)/(7)}(add,1)\rightarrow ^{(3,\bot)/(10)}(add,3)$


### B
* A sequence to get (mul,42):
	($\bot$,1) and then ($\top$,42) 


### C
transition system for the extended state machine:
$[(mode = add) \wedge (flip? = false) \wedge (mode'=add) \wedge (x= x+in) ]$ 
$\vee [(mode = add) \wedge (flip? = true) \wedge (mode'=mul) \wedge (x= x \cdot in) ]$
$\vee [(mode = mul) \wedge (flip? = false) \wedge (mode'=mul) \wedge (x= x \cdot in) ]$
$\vee [(mode = mul) \wedge (flip? = true) \wedge (mode'=add) \wedge (x= x + in) ]$


## Exercise 2
### A
This is not an inductive invariant since by looking at the initial state where x and y equals 1 which is not even

### B
this is not an inductive invariant since it is possible  

### C
$\varphi : (z=1 \wedge x=y) \vee (z=0 \wedge x=2y)$


## Exercise 3
### A
all values are integers 
![[Pasted image 20230612133108.png]]

### B
see exercise A


## Exercise 4
### A
E is reachable 

### B
(A, x=0, y=0)->(A, x=4, y=4)->(b,x=4,y=4)->(c,x=0, y=4)->(E,x=0,y=4)

### C
time is 4 and The witnessing sequence is above (exercise 4.B)

### D
$A_{entry} = \{x = 0 \wedge y=0\}$
$A_{delay} = \{x = y \wedge x\geq 0 \wedge x\leq 6\}$

$B_{entry} = \{x = y \wedge x\geq 2 \wedge x\leq 6\}$
$B_{delay} = \{x = y \wedge x\geq 2 \wedge x\leq 7 \}$

$C_{entry} = \{x = 0 \wedge y\geq 4 \wedge y\leq 6\}$
$C_{delay} = \{y\geq 4 \wedge y\leq 6 \wedge 4 \leq y-x \leq 6 \wedge x \geq 0\}$

### E
Guard to D should be weaken to $y\leq 4$
and guard to F should be weaken to $x \geq 2$


## Exercise 5
### A
here is the query `E<> time <=50 && Kim.Done && Juri.Done && Wang.Done && Jan.Done`

### B
it is satisfied and here is the schedule with the time = 37:
see appended file MSC.svg

### C
here is the query `E<> time <=20 && Kim.Done && Juri.Done && Wang.Done && Jan.Done`

### D
The query is not satisfied. the witness is the same MSC as in exercise B

### E
by running the fastest trace the best completion time is 37 mins as can be seen in the MSC in exercise B

### F
with the modification the new fastest completion time is 38 minutes 

### G
with the modification the new fastest completion time is 37 minutes

### H
with the modification the new fastest completion time is 52 minutes

### I
with the modification the new fastest completion time is 41 minutes


## Exercise 6
### A
quad controller:

   |$real: z_L \leq z \leq z_U$        |
		 |      $v_L \leq v \leq v_U$        |
\- F -> |\--------------------| -z-> 
	     |$\frac{d}{dt}z=v$                     | 
		 |$\frac{d}{dt}v=-9.81+\frac{1}{0.5}F$  |


controller:

-r-> | $F = K_p(R-z)$ | -F->
              ^
			   | z


### B