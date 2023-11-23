* Dynamic programming:
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

