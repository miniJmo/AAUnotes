![[Pasted image 20230607190507.png]]
CTL state formulas: 
* ψ ::= a | (ψ ∧ ψ) | (¬ψ) | (Eφ) | (Aφ)
	* where "a" is an atomic proposition and $\varphi$ is a CTL path formula 

CTL path formula:
* φ ::= $\Box \psi | \diamond \psi$  
	* where $\psi$ are CTL state formulas 

CTL formulas are CTL state formulas


# CTL semantics

Convention: For a path π = σ0 → σ1 → . . . , let π(i) denote $\sigma_i$

$\sigma \models a$ iff "a" is a label of $sigma$
![[Pasted image 20230607191758.png]]

example:![[Pasted image 20230607191832.png]]
![[Pasted image 20230607191952.png]]
more examples can be found in the slides