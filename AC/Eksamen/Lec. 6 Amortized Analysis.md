Goals:
* to understand what is amortized analysis, when is it used, and how it differs from the average-case analysis
* to be able to apple the techniques of the aggregate analysis, the accounting method, and the potential method to analyse operations on simple data structures

* Sequence of operations
	* the problem
		* we have a data structure
		* we perform a sequence of operations
			* operations may be of different types 
			* Depending on the state of the structure the actual cost of an operation may differ 
		* just analysing the worst-case time of a single operation may not say too much
		* we want the average running time of an operation (but from the worst-case sequence of operations)

# Amortized 
* Example data structure: a binary counter
	* operation: increment 
	* Implementation: An array of bits A[0..k–1]![[Pasted image 20230603155802.png]]
* How many bit-assignments do we do on average?
	* Let’s consider a sequence of n Increments 
	* Let’s compute the sum of bit assignments:
		* A[0] assigned on each operation: n assignments
		* A[1] assigned every two operations: n/2 assignments
		* A[2] assigned every four ops: n/4 assignments
		* A[i ] assigned every 2i ops: n/2i assignments![[Pasted image 20230603160008.png]]
* thus , a single operation takes 2n/n = 2 = O(1) **amortized** time

## Aggregate analysis
* a simple way to do amortized analysis
	* treat all operations equally
	* compute the worst-case running time of a sequence of n operations
	* divide by n to get an amortized running time

### example
* Another way of looking at it (proving the amortized time):
	* To assign a bit, I have to pay $1
	* when I assign "1", I pay $1, plus I put $1 in my "savings account" associated with that bit.
	* When I assign "0", I can do it using a dollar from the savings account on that bit
	* how much do I have to pay for the increment(A) for this scheme to work?
		* Only one assignment of "1" in the algorithm. Obviously, $2 will always pay for the entire operation.                                        ![[Pasted image 20230603160539.png]]

### Principle of the accounting method 
* 1. Associate credit account with different parts of the structure 
* 2. Associate amortized costs with operations and show how they credit or debit accounts
	* Different costs may be assigned to different operations
* Requirement (c- real cost, $\hat{c}$ - amortized cost):                                    ![[Pasted image 20230603161040.png]] 
* This equivalent to requiring that the sum of all credits in the data structure is non-negative after any sequence of operations
* 3. show that this requirement is satisfied 

#### stack example
* Start with an empty stack and consider a sequence of n operations: Push, Pop, and Multipop(k). 
	* What is the worst-case running time of an operation from this sequence? 
	* 1. Let’s associate an account with each element in the stack 
	* 2. After pushing an element, put a dollar into the account associated with it, 
		* then Pop and Multipop can work only using money in the accounts (amortized cost 0) • Push has amortized cost 2 
	* 3. The total credit in the structure is always ≥ 0 
	* Thus, the amortized cost of an operation is O(1)

### Potential method
* We can have one account  associated with the whole structure:
	* we call it a potential
	* it's a function that maps a state of the data structure after operation i to a number: $\phi$(D$_i$)
		* $\hat{c}_i = c_i + \phi(D_i) - \phi(D_{i-1})$
* The main step of this method is defining the potential function
	* Requirement: $\phi(D_n)-\phi(D_0)\geq0$
* Once we have $\phi$, we can complete the amortized costs of operations

* binary counter example: ![[Pasted image 20230603163050.png]]

* it is possible analyse the counter with potential method even if the doesn't start at 0
	* see slide 12 in lec 6

## Dynamic tables
* it can be a good idea to use a dynamic table
	* The table that expands and contracts as necessary when new elements are added or deleted
		* Expands when insertion is done and the table is already full
		* Contracts when deletion is done and there is “too much” free space
	* Contracting or expanding requires relocating
		* allocate new memory space
		* copy all elements into the new space
		* free old space
	* worst-case time for insertion and deletions:
		* without relocating: O(1)
		* with relocating: O(m), where m is the number of elements in the table

* requirements:
	* Load factor
		* num - current number of elements in the table
		* size - the total number of elements that can be stored in the allocated memory
		* load factor $\alpha$ =num/size
	* It would be nice to have there two properties
		* Amortized cost of insert and delete constant 
		* the load factor is always above some constant


## Aggregate analysis /accounting
* the "right" way to expand - double the size of the table
	* Let's do an aggregate analysis
	* The cost of the i-th insertion is:
		* i, if i-1 is an exact power of 2
		* 1, otherwise
	* Let's sum up ![[Pasted image 20230603165101.png]]
	* The total cost of n insertions is then < 3n
	* Accounting method gives the intuition: 
		* Pay $1 for the inserting the element
		* Put $1 into element's account for reallocating it later
		* Put $1 into the account of another element to pay for a later relocation of that element![[Pasted image 20230603165312.png]]

* potential function![[Pasted image 20230603165407.png]]

* Deletions: what if we contract whenever the table is about to get less than half full?
	* problem: we want to avoid doing re-allocations often without having accumulated "the money" to pay for that
	* Idea: Delay contraction
		* contract only when num = size/4
		* second requirement still satisfied $\alpha \geq 1/4$ 
	* how do we define the potential function?![[Pasted image 20230603170016.png]]
	* It is always non-negative
	* 