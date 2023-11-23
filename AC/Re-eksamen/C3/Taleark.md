* Time complexity:
	* decidable $\neq$ realistically solvable 
		* too much time or memory
	* complexity theory
		* general conclusions on time requirements 

* The class P
	* languages decidable in polynomial time 
		* deterministic single tape TM
	* proof language Lp in P
		* provide TM M such that
			* L(M) = Lp 
			* M is a polynomial time decider

* The class NP
	* languages decidable in polynomial time
		* Nondeterministic single tape TM
	* show a language is in NP
		* verify with certificates
		* a verifier is a decider V 
			* such that L = {w | V accepts ⟨w, c⟩ for some string c} 
		* c is called a certificate of proof
		* a verifier = polynomial 
			* if it runs in polynomial time on w
		* language is polynomial verifiable language if it has a polynomial time verifier.

* P vs. NP
	* **P** = memberships *decided* quickly
	* **NP** = memberships *verified* quickly
	* both in ExpTime
	* P = NP ?

* polynomial time reduction
	*  when A efficiently reduced to B
	* an efficient solution to B can solve A efficiently

* NP-completeness 
	* first NP-hardness
		* language B is NP-Hard iff
			* for every A in NP we have $\leq_P$ B.
		* as hard as all other problems in NP
		* B may not in NP
	* NP-complete
		* B is NP-complete iff
			* B in NP
			* for every A in NP we have $\leq_P$ B.






