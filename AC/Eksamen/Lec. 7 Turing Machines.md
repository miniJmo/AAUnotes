* can every problem be solved (efficiently) by an algorithm?
* actually what is an algorithm? And what is a problem? And what does efficiently mean?
* Can an algorithm solving A help me solving problem B?
* Is is harder to compute something than to verify something?

Goal:
* What problems can be solved algorithmically (with a computer)?

# Motivation
What to do when you can't find an efficient algorithm?
* Computability: We can prove that some problems cannot be solved by computers
* Complexity: We can prove that some problems cannot be solved in polynomial time by computers (unless P=NP)
Computability/complexity is about understanding some fundamental truth about the (computational) limitations of our universe!

# Languages
* what is an algorithm? and what is a problem?

Decision problems:
* A decision problem is a yes/no question on an (typically infinit) set of inputs
	* example: Given $p \in \mathbb{N}$, is $p$ prime?

Formal languages: 
* Let $\Sigma$ be a finite, nonempty set called alphabet
* A string or word $w$ over $\Sigma$ is a finite sequence of symbols from $\Sigma$.
* An empty string is denoted $\epsilon$. 
* A concatenation of strings $w_1$ and $w_2$ is a string $w_1w_2$.
* A length of a string $w$ is the number of symbols in $w$ and it is denoted by $|w|$.
* The set of all strings over $\Sigma$ is denoted by $\Sigma^*$.
* A Language $L$ over $\Sigma$ is any subset of $\Sigma^*$, i.e., $L\subseteq \Sigma^*$.

Operations on languages:![[Pasted image 20230603184700.png]]
* decision problems as languages.
	* Given $p \in \mathbb{N}$, is $p$ prime?
		* $L_{primes} = \{w \in \{0,...,9\}*| w$ is prime$\}$

# Turing Machines
* What problems can be solved algorithmically (with a computer)?
* Pushdown automata (PDA)
	* extends FSA(finte state automata) with a stack
	* has infinite memory but can only access it in a limited way
	* PDA represent context free languages

* Computations can be done with input/output tapes![[Pasted image 20230603192430.png]]
* Essentially a finite-state automaton with unbounded memory
* Program ends with $q_{accept}$ or $q_{reject}$.

* Turing Machines defines the limits of computation
* Definition:
	* A Turing machine is a 7-tuple $M = (Q,\Sigma,\Gamma,\delta,q_0,q_{accept},q_{reject})$:
		* Q is a finite set of states
		* $\Sigma$ is a finite input alphabet ($\sqcup \notin \Sigma$ )
		* $\Gamma$ is a finite tape alphabet ($\sqcup$ = empty/blank symbol, $\sqcup \in \Gamma$ and $\Sigma \subset \Gamma$)
		* $\delta$: $Q\times \Gamma \rightarrow Q\times \Gamma \times \{L,R\}$ is the transition funtion,
		* $q_0 \in Q$ is the start state
		* $q_{accept} \in Q$ is the accept state, and
		* $q_{reject} \in Q$ is the reject state, where $q_{accept} \neq q_{reject}$ ![[Pasted image 20230603193646.png]]

* example of a transition function:![[Pasted image 20230603194005.png]]

## Configuration
Let M be a TM.
informally, a configuration consists of 
* the current control-state
* the current control tape content, and
* the current head position.

formal definition:
A configuration of a TM is a string $uqv$ where
* $u \in \Gamma^*$ is the initial part of the tape,
* $q\in Q$ is the current state,
* $v \in \Gamma^*$ is the final part of the tape and the head points at the first symbol of $v$.

computation of a Turing machine
![[Pasted image 20230603195327.png]]

acceptance of a string by a Turing machine![[Pasted image 20230603195410.png]]

* Decider:
	Assume that a TM M computes from the initial configuration $C_1 = q_0w$ (note that this computation is deterministic)
	* there are three possible outcomes of running M on w:
		* C1, C2, . . . , Ck ends in accept configuration Ck, or
		* C1, C2, . . . , Ck ends in reject configuration Ck, or
		* C1, C2, . . . does not terminate (loops).

	* formal definition:
		* A TM M which for any input string w always halts (either in accept or reject configuration) is called a decider.

# Recognisable and Decidable languages
* What problems can be solved algorithmically?
	* what do we mean when we say that an algorithm soles a problem?

Language definition:
* The language recognised by a TM M, or simply the language of M is:       $L(M) = \{w\in \Sigma^* | M$ accepts $w\}$ 

recognisable language definition:
* A language $L\subseteq \Sigma^*$ is recognisable if there exists a TM M such that M recognises L, i.e., $L =L(M)$

Decidable language definition:
* A Language $L\subseteq \Sigma^*$ iss decidable if there exists a TM M such that M is a decider and M recognises L,i.e., $L=L(M)$![[Pasted image 20230603201652.png]]

Computational function:
* Idea: Turing machines can also compute functions $f:\Sigma^* ->\Sigma^*$.

computational function definition:
* A function $f:\Sigma^* \rightarrow \Sigma^*$ is a computational function iff (if and only if) there exists a TM $M_f$ which on any given input $w \in \Sigma^*$
	* always halts, and
	* leaves just $f(w)$ on its tape.![[Pasted image 20230603202201.png]]



