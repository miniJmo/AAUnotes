* Turing Machines
	* what problems can be solved algorithmically 
	* Church-Turing Thesis:
		* Algorithms = Turing Machines
		* not proven (but nothing better)

	* works by 
		* scanning input
		* compute action, dependent on state

* multitape Turing Machines
	* same but different transition function
		* supports multiple tapes

	* are equivalent to single tape TMs
		* can be simulated 
			* each configuration has an equivalent 
			* each transition has an equivalent sequence 

* Nondeterministic Turing Machines
	* searching multiple computational paths in parallel
	* different transition function:
		* add a power set (multiple paths) 
	* Every deterministic TM is also a nondeterministic TM.

	* computation tree:
		* of all reachable configurations

	* can be simulated by 3-tape deterministic TM

* Deciablility  
	* how do algorithmic problems correspond to languages?
	* *Algorithmically solvable* problems identical to *decidable* languages

	* problem = solvable 
		* if its language is decidable 
	* proof decidable language:
		* specify TM M, recognises L
		* show M is a Decider

* acceptance problem
	* does M accept w?![[Pasted image 20230604111420.png]]
	* **Theorem**:
		* The language $A_{TM}$ is undecidable 
	* proof:
		* by contradiction:
		* assume decider H
			* accepts when accept, reject when no accept
		* build D from H also a decider:
			* run H on  $\langle M \langle M \rangle \rangle$ 
			* H accepts then reject, H reject then accept
		* run D on $\langle D \rangle$?
			1. D accepts, but H rejects $\langle D \langle D \rangle \rangle$ and hence didn't accept, contradiction 
			2. same for reject
		* D and H can't exist 
		* means $A_{TM}$ is undecidable 
	
*Diagonalisation* and $A_{TM}$![[Pasted image 20230604112819.png]]
