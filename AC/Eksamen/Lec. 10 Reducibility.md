Wouldn’t it be great if we could show that L is undecidable by providing a TM? 
* Reduction to the rescue!


# Reduction 
intuition:![[Pasted image 20230604120008.png]]

Informal definition:
* A problem $A$ is reducible to problem $B$ iff the solution to problem $B$ can be used to solve the problem $A$.
	* this means that solving A cannot be more difficult than solving B.

A reduced to B means that:
* if B is decidable then A is decidable too, and
* if A is undecidable then B is undecidable too.

The way we will use reducibility:
* If we can reduce e.g. $A_{TM}$ to some other problem (language) B, then B is undecidable.

proof structure to show undecideability:
* proof by contradiction![[Pasted image 20230604120815.png]]
* In the proof we provided a reduction from an undecidable language A to the language B. Hence B is undecidable too.

Problem: ”Given a TM M and a string w, does M halt on w?"![[Pasted image 20230604121403.png]]
* theorem: 
	* the language $HALT_{TM}$ is undecidable 
	* proof: We reduce $A_{TM}$ to $HALT_{TM}$.
		* ![[Pasted image 20230604122711.png]]


what about an empty language?
Problem: "Given a TM M is the language of M empty?"![[Pasted image 20230604122955.png]]
* Theorem: The language $E_{TM}$ is undecidable.
* proof by reduction
	* ![[Pasted image 20230604123012.png]]


![[Pasted image 20230604123650.png]]![[Pasted image 20230604123718.png]]

Rice's Theorem:
* Every language P which is a nontrivial property of Turing machine languages is undecidable.

# Mapping Reduction
proof template to show undecidability by reduction:
* We know that language A is undecidable. By reducing A to B we want to show that the language B too.
	* By contradiction assume that we have a decider $M_B$ for B
	* Using $M_B$ we construct a decider $M_A$ for the language A![[Pasted image 20230604124442.png]]
	* We know that $M_A$ cannot exist, so $M_B$ cannot exist either.
	* conclusion: The language B is undecidable 

## Computable Function
Idea: Turing machine can also compute functions $f: \Sigma^* \rightarrow \Sigma^*$.
Definition:
* A funciton $f: \Sigma^* \rightarrow \Sigma^*$ is a computable function iff there exists an TM $M_f$ which on any given input $w \in \Sigma^*$ 
	* always halts, and
	* leaves just $f(w)$ on its tape.

### example 
![[Pasted image 20230604125700.png]]
![[Pasted image 20230604125717.png]]

## Mapping 
Definition:
* Let $A, B \subset \Sigma^*$. We say that language A is mapping reducible to language B, written $A\leq_m B$, iff
	* There is a computable function $f: \Sigma^* \rightarrow \Sigma^*$ such that 
	* for every $w \in \Sigma^*$:
		* $w \in A$ iff $f(w) \in B$
		* or equivalently: if $w \in A$ then $f(w) \in B$, and if $w \notin A$ then $f(w) \notin B$.![[Pasted image 20230604130656.png]]
		* $f$ does not need to be invertible or bijective ($A\leq_m B \neq B\leq_m A$) 
		* this is called many to one reducibility 

* example: ![[Pasted image 20230604132737.png]]

* Results of mapping reducibility:
* Assume that $A \leq_m B$. Then: 
	* If B is decidable then A is decidable. 
	* If A is undecidable then B is undecidable. 
	* If B is recognizable then A is recognizable. 
	* If A is not recognizable then B is not recognizable.
	* $\bar{A}\leq_m\bar{B}$


* Turing Reducibility ($A\leq_TB$): given an “oracle” for B, construct a TM for A 
	* →Useful to show that B is undecidable
* Mapping Reducibility ($A\leq_mB$): map input from A to input from B 
	* →Useful to show that B is undecidable or unrecognizable
theorem: If $A\leq_mB$ then $A\leq_TB$


# Beyond Recognisable Problems
The $EQ_{TM}$ problem:![[Pasted image 20230604143806.png]]

Theorem: 
* The language $EQ_{TM}$ is neither recognisable nor co-recognisable 
proof:
* We show that 
	* $\bar{A_{TM}} \leq_m EQ_{TM}$, and![[Pasted image 20230604144102.png]]
	* $\bar{A_{TM}} \leq_m \bar{EQ_{TM}}$.![[Pasted image 20230604144136.png]]
![[Pasted image 20230604144221.png]]


# Post Correspondence Problem (PCP)
A PCP instance over $\Sigma$ is a finite collection P of dominos$$P = \{[\frac{t_1}{b_1}], [\frac{t_2}{b_2}],\cdots,[\frac{t_k}{b_k}]\}$$
Where for all $i, 1 \leq i \leq k,t_i,b_i \in \Sigma^*$
![[Pasted image 20230604145007.png]]

![[Pasted image 20230604145337.png]]

Take away from PCP: 
* Not all undecidable problems have something directly to do with TMs or other models of computation!
* Mapping reduction is not always between TM descriptions and can be creative
* PCP is also useful to apply reduction 

### Example 
![[Pasted image 20230604145036.png]]

