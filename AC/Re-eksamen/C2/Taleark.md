what makes Decidable, Recognizable, Co-Recognizable Languages, Reductions
How to show that a language is undecidable via Reduction

okay first of all what does Recognisable mean?
* When a language is recognisable then:
	* If $w \in L$ then M run on w will *halt in accept state*
	* If $w \notin L$ then M run on w will *reject or loop*.
* Co-recognisable language
	* *reverse* of recognisable 

* what makes a language Decidable?
	* it always *terminate* aka. accept or reject. It *cannot* loop
	* aka. both co- & recognisable 


* Reductions
	* Reduction is a way oh showing that problems can be reduced to other problems
	* A problem $A$ *is reducible to problem* $B$ iff the solution to problem $B$ can be used to solve the problem $A$.
		* this means that solving $A$ cannot be more difficult than solving $B$.

	* A reduced to B means that:
		* if B is *decidable* then A is decidable too, and
		* if A is *undecidable* then B is undecidable too.


*proof* structure to show undecideability:
* proof by contradiction:
	* We want to show that a language $B$ is undecidable using the fact that we already know that the language $A$ is undecidable
		1. Assume for a while that we have a decider $M_B$ for the language $B$ 
		2. Using $M_B$ we conduct a decider $M_A$ for the language $A$
		3. Because we know that $M_A$ cannot exist ($A$ is undecidable), this implies that $M_B$ cannot exist either.
		4. Conclusion is that the language $B$ is undecidable
* In the *proof* we provided a reduction from an undecidable language $A$ to the language $B$. Hence $B$ is undecidable too.