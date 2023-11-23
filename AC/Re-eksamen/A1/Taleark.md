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


* Data compression 
	* want to compress a string 
	* wanna achieves minimal length coded text
	* store in binary-tree
		* fast look up
		* nodes contain the frequencies 
		* leaves represent characters 
	* The cost of coding a tree T:
		* $B(T) = \sum _{c \in C} f(c)d_T(c)$
		* C - The alphabet
		* f(c) - frequency of c
		* $d_T$ - depth of c 
		
		* optimal tree - the one that minimises B(T)

* the Huffman algorithm, 
* takes a sting of characters
* builds the code tree bottom up. Consider a forest of trees:
	* initially - one separate node for each character.
	* in each step - join two trees into a larger tree
	* Repeat this until one tree remains.
	* which trees join?
		* greedy choice - the trees with the smallest frequencies!![[Pasted image 20230602180225.png]]


