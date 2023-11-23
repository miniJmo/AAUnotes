

# Algorithm Complexity
* trying to relate what problems are easier or harder
* In Turing machines
	* Time = the number of computation **steps**
	* Memory = the number of used **tape cells**
* This course focus on Time complexity

* we want to make claims that are robust 
	* worst time complexity

* standard time complexity stuff aka big o nation 

# Complexity Classes
A complexity class is a **set of computational problems** of related resource-based complexity 

![[Pasted image 20230418131759.png]]
* TIME the class of languages that are decidable by TMs running time $O(t(n))$
$$TIME(n) \subset TIME(n^2) \subset \cdots \subset TIME(2^n)\subseteq \cdots $$

![[Pasted image 20230418144017.png]]

* Relationship between $k$-tape TMs and 1-tape TMs
	* Every time a $k$-tape TM does one step then it requires two passes over the 1-tape TM
![[Pasted image 20230418134024.png]]

![[Pasted image 20230418135846.png]]

# The Class P
![[Pasted image 20230418135917.png]]
* The class P is **robust** (the class remains the same even if we choose some other deterministic model of computation).
* The class P roughly corresponds to the class of problems **realistically solvable** on a computer