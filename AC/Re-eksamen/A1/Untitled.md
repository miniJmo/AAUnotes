* Greedy algorithms what are they?
	* A *greedy* algorithm is made for solving optimisation problems, by picking what looks to be the best choice at the moment  
		* *making local optimal choice, to get global optimal solution*
		* Optimisation problem:
			* there are two things we need to find
			* compute the optimum value of the problem
			* and construct an object that has optimum value (proof of value)

	* for optimisation problems 
		* local choice 
		* global solution 
	* optimisation problems:
		* compute value
		* construct object 

* how do greedy algorithms work?
	* A greedy algorithm works by making these *greedy choices*.
	* But insure an optimal solution had been found we need to look if:
		* comply with the optimal substructure property 
			* To be sure that the algorithm finds an optimal solution, the *optimal sub-structure* property has to hold 
				* **If** an optimal solution includes a choice that we consider **then** it includes optimal solutions to the sub-problems that this choice generates
				* **But** not always! Longest simple unweighted path example - no optimal sub-structure
					* the sub-problems have to be *independent*
		* and then if they comply with the greedy choice property 
			* that our local choice is apart of a global optimal solution


	* greedy choices
	* insure optimal solution
		* optimal substructure 
			* choice leads to optimal solution 
			* so will the sub-problems
			* but gotta be independent 
		* greedy choice property 
			* local choice in global solution 



	* But how can we make sure that we choose "the best choice"? 
		* It all depends on the problem you are trying to solve  
		* for example the activity problem
			* it is what activity ends first 

	* what is the best choice
		* depends on the problem
		* activity problem = activity that ends first




* Greedy algorithms what are they?
	* for optimisation problems 
		* local choice 
		* global solution 
	* optimisation problems:
		* compute value
		* construct object 


* how do they work?
	* greedy choices
	* insure optimal solution
		* optimal substructure 
			* choice leads to optimal solution 
			* so will the sub-problems
			* but gotta be independent 
		* greedy choice property 
			* local choice in global solution 

	* what is the best choice
		* depends on the problem
		* activity problem = activity that ends first

* the Huffman algorithm, 
* takes a sting of characters
* builds the code tree bottom up. Consider a forest of trees:
	* initially - one separate node for each character.
	* in each step - join two trees into a larger tree
	* Repeat this until one tree remains.
	* which trees join?
		* greedy choice - the trees with the smallest frequencies!![[Pasted image 20230602180225.png]]