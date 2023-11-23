Is a Turing Machine everything we can do? What about... 
* parallel computing? 
* quantum computing? 
* neural networks/machine learning?
* some weird technology that we haven’t invented yet? 

Robustness definition:
* A model of computation is robust if no reasonable extension increases its power.
* (Turing machines are very robust)


# Church-Turing Thesis
Alonzo church invented $\lambda$-calculus and Turing machines were shown equivalent.

Church-Turing Thesis:
* **Algorithms** (informal notion) **=** **Turing machines** (formal, mathematical, concept)

this thesis cannot be proved, but nothing more powerful than a TM has been found so far.

Turing-complete:
* A model of computation id Turing-complete if it can simulate a TM -> can do everything that a TM can do


# Multitape TM
Multitape Turing machine definition: 
* A $k$-tape TM is a 7-tuple $M = (Q,\Sigma,\Gamma,\delta,q_0,q_{accept},q_{reject})$ where
	* $\delta$: $Q\times \Gamma^k \rightarrow Q\times \Gamma^k \times \{L,R\}^k$ 
	and the rest is the same as before.

remark: 1-tape TM is exactly our original definition of TM.

* Configuration: 
	* a control state, plus the content af all $k$ tapes together with the position of $k$ heads.
* Initial configuration: 
	* input string written on the first tape, all other tapes are empty (contain the blank symbol s($\sqcup$))
* Computational step: 
	* all heads can move independently.

## example of 3- Tape Turing Machince
![[Pasted image 20230603210943.png]]
![[Pasted image 20230603210952.png]]
![[Pasted image 20230603211004.png]]


## Equivalence of 1-tape and $k$-tape TM
Theorem:
* Every $k$-tape TM is equivalent to 1-tape TM.
	Corollaries:
	* A language is recognisable iff it is recognised by some multitape Turing machine
	* A language is decidable iff it is recognised by some multitape Turing machine which is a decider.

* Let $M_k = (Q,\Sigma,\Gamma,\delta,q_0,q_{accept},q_{reject})$ be a $k$-tape TM.
* we construct a TM
* $M = (Q,\Sigma,\Gamma,\delta,q_0,q_{accept},q_{reject})$ such that it simulates $M_k$
	* For each configuration $C^k_i$ of $M_k$ there exists an equivalent configuration of $\mathcal{M}, C_i$
	* For each transition $C^k_i \rightarrow C^k_{i+1}$ in $M_k$ we have a sequence $C_i \rightarrow \cdots \rightarrow C_{i+1}$ 
* We are free to choose $Q,\Sigma,\Gamma$ and $\delta$

* **To see an example of this look from slide 100 (21) in slides for this lecture**

# Nondeterministic TM
nondeterministic Turing machine definition:
* A nondeterministic TM is a 7-tuple $M = (Q,\Sigma,\Gamma,\delta,q_0,q_{accept},q_{reject})$ where
	* $\delta$: $Q\times \Gamma \rightarrow 2^{Q\times \Gamma \times \{L,R\}}$ 
* and the rest is the same as before.

Remark: Every deterministic TM is also a nondeterministic TM.
* configuration and initial configuration is the same as before

* example:![[Pasted image 20230603215255.png]]
* computation tree: a tree of alle the configurations reachable from the initial one. The tree can have infinite branches.

## Acceptance Condition
Acceptance condition of a Nondeterministic TM:
* A nondeterministic TM $\mathcal{M}$ accepts a string $w$ if the computation tree for $\mathcal{M}$ and $w$ contains at least one accepting configuration.

* A nondeterministic TM is a decider if for any given input every branch in the computation tree is finite (accepts or rejects).

## Equivalence of Non- and Deterministic TM
Theorem:
* Every nondeterministic Turing machine can be simulated by a (deterministic) 3-tape Turing machine (and therefore by a standard Turing machine)

Deterministic 3-tape TM $\mathcal{M}_3$ simulates nondeterministic TM $\mathcal{M}'$:
* for every configuration of $\mathcal{M}$' there is a configuration of $\mathcal{M}_3$.
* every configuration in the computation tree of $\mathcal{M}'$ and $w$ is reached by the unique run of $\mathcal{M}_3$ on $w$ (but possibly more auxiliary configurations as well).
* $\mathcal{M}_3$ accepts if and only if accepting configuration of $\mathcal{M}'$ is reached.
* $\mathcal{M}_3$ rejects if and only if computation tree is finite and no accepting configuration of $\mathcal{M}'$ is reached.

Corollary:
* A language is recognisable iff it is the language of some nondeterministic Turing machine.
* A language is decidable iff it it the language of some nondeterministic decider.


# Decidability 
* how do algorithmic problems correspond to languages?
	* Algorithmically solvable problems $\equiv$ decidable languages.

A problem is solvable id its language is decidable. How do we show that a language is decidable?
* Specify a TM $M$ that recognises $L$ (or a $k$-tape TM; or a nondeterministic TM)
* Show that $M$ is a decider (halts on every input)

Theorem: 
* The Class of decidable languages is closed under intersection, union, complement, concatenation and Kleene star.

* what does closed under mean?
	* if $L_1$ and $L_2$ are decidable languages then $L_1 \cap L_2$, $L_1 \cup L_2$, $\bar{L_1}$, $L_1.L_2$ and $L_1^*$ are decidable too.![[Pasted image 20230604094638.png]]

Theorem:
* The Class of recognisable languages is closed under intersection, union, concatenation and Kleene star.
	* BUT not under complement 



