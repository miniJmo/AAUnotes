* Dynamic programming what is that
	* they are used to solve optimisation problems
		* there are two things we need to find
			* compute the optimum value of the problem
			* and construct an object that has optimum value (proof of value)

	* for optimisation problems
		* local choice 
		* global solution 

	* The structure of dynamic programming is 
		* first *choices* has to be made to find the optimal solution
		* each *choice generates* a number of *sub-problems
		* which choice to make is decided by looking at all *possible choices* and the solutions to sub-problems that each choice generates.
		* The *solution* to a specific sub-problem is used many times in the algorithm 
			* sub-problems are overlapping 

	* structure 
		* make choices to find optimal solution 
		* choices generates sub-problems
		* sub-problems share solutions (overlap)

		* In other words:
		* *First*, think how to compute the value of a variable that we optimise
			* *Then*, augment your algorithm to remember the choices made.
			* *Finally*, the choices can be traced back to build an optimal solution corresponding to an optimal value.

	* so how do we construct/design a dynamic programming algorithm?
	*  *Recurrence for the optimal value*
		* which choices have to be considered in each step of the algorithm
		* what are the sub-problems?
		* how are the trivial sub-problems solved?
		* which order do we have to solve the sub-problems 
			* or write a memoized version of the algorithm
	* *Constructing a solution*
		* Remember the optimal choices made
		* Use the remembered choices to construct a solution 

	* construction
		* Recurrence 
			* consider choices
			* sub-problems 
			* and how are they solved
			* order of sub-problems
		* Constructing a solution 
			* Remember choices
			* use choices to solution


* lastly to be sure that we have found a optimal solution the *optimal sub-structure* property has to hold 
	* **If** an optimal solution includes a choice that we consider **then** it includes optimal solutions to the sub-problems that this choice generates
	* **But** not always! Longest simple unweighted path example - no optimal sub-structure
		* the sub-problems have to be *independent*

* optimal sub-structure
	* choice leads to optimal solution 
	* so will the sub-problems
	* but gotta be independent 

* how does it work 
	* **edit distance example (making a word into another word)**


	* for optimisation problems:
		* compute value
		* construct object 


	* structure 
		* make choices to find optimal solution 
		* choices generates sub-problems
		* sub-problems share solutions (overlap)

	* construction
		* Recurrence 
			* consider choices
			* sub-problems 
			* and how are they solved
			* order of sub-problems
		* Constructing a solution 
			* Remember choices
			* use choices to solution
	
	* optimal sub-structure
		* choice leads to optimal solution 
		* so will the sub-problems
		* but gotta be independent 

* example 
	* Edit distance 
	* turn one string s into t in the smallest steps
	* we can
		* replace
		* insert
		* delete
	* the choice is edit one end of s
	* trivial sub-problems are empty strings
	* look at the choices that takes the least steps ![[Pasted image 20230602151710.png]]
