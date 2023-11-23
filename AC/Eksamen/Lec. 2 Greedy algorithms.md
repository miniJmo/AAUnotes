Goals:
* to understand the principles of the greedy algorithm design technique
* to understand the example greedy algorithms for activity selection and Huffman coding, to be able to prove that these algorithms find optimal solutions 
* to be able to apply the greedy algorithm design technique 

# Principles of greedy algorithms 
* input:
	* A set of n activities, each with start and finish times: A[i].s and A[i].f
* Output.
	* The largest subset of mutually compatible activities 
		* Activities are compatible if their intervals do not intersect![[Pasted image 20230602155956.png]]

## Greedy choice
* What if we could choose "the best" activity (as for now) and be sure that it belongs to an optimal solution
	* we wouldn't have to check out all these sub-problems and consider all currently
* Idea: Choose the activity that finishes first!
	* Intuition: leave as much time as possible for other activities 
		* then solve only one sub-problem for the remaining compatible activities 
		* (have sentinel activity A[0].f = 0 - before all other)![[Pasted image 20230602163551.png]]

* Iterative algorithm![[Pasted image 20230602163836.png]]

## Greedy choice property 
* Does it find an optimal solution?:
	* we have to prove the optimal sub-structure property 
	* we have to prove the greedy choice property i.e., that our locally optimal choice a1 belongs to some globally optimal solution
		* let A be an optimal solution and x be an activity with smallest finishing time in A
		* a1.f $\leq$ x.f as a1 is the activity with the smallest finishing time overall.
		* thus, we can replace x with a1 in A to get a valid solution of the same size!
	 * greedy exchange proof


* The challenge is to choose the right interpretation of "The best choice"
	* how about the activity that starts first?
		* show a counter-example 
	* the shortest activity?
	* the activity that overlaps the smallest number of the remaining activities?![[Pasted image 20230602172636.png]]
	* ![[Pasted image 20230602172814.png]]
		* The second row gives the maximum-size set of mutually compatible activities, but it does not include the activity with the smallest overlaps, i.e., the one with 2.

# Data compression / Huffman 
* Data compression problem - strings S and S':
	* S->S'->S, such that |S'|<|S|
* test compression by coding with variable-length code:
	* Obvious idea - assign short codes to frequent characters: "abracadabra"![[Pasted image 20230602174133.png]]
	* how much do we save in this case?
![[Pasted image 20230602181132.png]]
* we can store all these code-words (variable-length code) in a binary tree
	* for fast look up/decode
	* each node contains the sum of the frequencies of all descendants 
	* leaves represents characters 

## Huffman 
* the Huffman algorithm, builds the code trie bottom up. Consider a forest of trees:
	* initially - one separate node for each character.
	* in each step - join two trees into a larger tree
	* Repeat this until one tree (trie) remains.
	* which trees join?
		* greedy choice - the trees with the smallest frequencies!![[Pasted image 20230602180225.png]]

* correctness of Huffman
	* Greedy choice property
		* Let x, y - two characters with lowest frequencies. 
		* Then there exists an optimal prefix code where codewords for x and y have the same length and differ only in the last bit
	* Optimal sub-structure property:
		* let x, y - characters with minimum frequency
		* C' = C-{x,y}$\cup$ {z}, such that f(z)=f(x)+f(y)
		* Replace leaf z in T' with internal node with two children x and y
		* The result tree T is an optimal code trie for C

# Greedy algorithms tldr
* are used for optimization problems
	* a number of choices have to be made to arrive at an optimal solution.
	* At each step, make the "locally best" choice, without considering all possible choices and solutions to sub-problems induced by these choices (compared to DP)
	* After te choice, only one sub-problem remains (smaller than the original)
	* Top-down instead of bottom-up dynamic programming
* Greedy algorithms are usually sort or use priority queues.

* First, one has to prove the optimal sub-structure property
	* the simple “cut-and-paste” argument may work
	* Not always possible (sign that it is a hard problem):
		* Longest (vs. shortest) simple unweighted path
		* Maximum clique in a graph (vs. activity selection)

* The main challenge is to decide the interpretation of “the best” so that it leads to a global optimal solution, i.e., you can prove the greedy choice property
	* The proof is usually constructive: takes a hypothetical optimal solution without the specific greedy choice and transforms into one that has this greedy choice.
	* Or you find counter-examples demonstrating that your greedy choice does not lead to a global optimal solution.


