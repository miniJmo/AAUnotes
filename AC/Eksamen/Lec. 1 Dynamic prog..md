Goals of the lecture:  
- to understand the principles of dynamic programming;  
- to understand the example dynamic programming algorithms for activity selection and edit distance;  
- to be able to apply the dynamic programming algorithm design technique.

# Dynamic programming
A Technique for solving optimisation problems
#### optimisation problems
* can be finding the shortest route from A to B

* there are two things we need to:
	* compute optimum value
		* length of a route 
	* Construct an object that has optimum value (i.e. proof of the value)
		* route, etc.
#### Structure:
* *choices* has to be made to find the optimal solution
* each *choice generates* a number of *sub-problems
* which choice to make is decides by looking at all *possible choices* and the solutions to sub-problems that each choice generates.
* The *solution* to a specific sub-problem is used many times in the algorithm 
	* sub-problems are overlapping 

* *First*, think how to compute the value of a variable that we optimise
	* *Then*, augment your algorithm to remember the choices made.
	* *Finally*, the choices can be traced back to build an optimal solution corresponding to an optimal value.

#### DP algorithm Design roadmap
* construction:
	* *Recurrence for the optimal value*
		* which choices have to be considered in each step of the algorithm
		* what are the sub-problems?
		* how are the trivial sub-problems solved?
		* which order do we have to solve the sub-problems 
			* or write a memoized version of the algorithm
	* *Constructing a solution*
		* Remember the optimal choices made
		* Use the remembered choices to construct a solution 

* analysis:
	* how many different sub-problems are there?
	* how many choices have to be considered in each step?

#### Example of a DP
![[Pasted image 20230602150918.png]]
![[Pasted image 20230602150934.png]]
![[Pasted image 20230602150945.png]]
![[Pasted image 20230602151050.png]]
* Recurrence 
![[Pasted image 20230602151213.png]]
* Algorithm memoized
![[Pasted image 20230602151325.png]]
* alg
![[Pasted image 20230602151642.png]]
* run the algorithm 
![[Pasted image 20230602151710.png]]


#### Elements of DP
* To be sure that the algorithm finds an optimal solution, the *optimal sub-structure* property has to hold 
	* **If** an optimal solution includes a choice that we consider **then** it includes optimal solutions to the sub-problems that this choice generates
	* **But** not always! Longest simple unweighted path example - no optimal sub-structure
		* the sub-problems have to be *independent*

* Maybe talk about the longest path example?