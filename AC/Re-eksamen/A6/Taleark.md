* amortised analysis
	* average runtime of a set of operations on a data structure
	* (worst case for each)

* multiple methods
	* accounting method
		* principles 
			1. associate credit account with structure parts
			2. associate amortised costs with operations
				* requirement (c- real cost, $\hat{c}$ - amortized cost):                                    ![[Pasted image 20230603161040.png]]
			3. satisfy requirement 

		* stack example
			* empty
			* operations: push, pop, multipop(k)
			1. accounts for each element
			2. push = put 1$ on element acc.
				* pop, multipop takes 1$ = amortised cost 0
				* Push = amortised cost 2
			3. total credit always $\geq$ 0
			* Thus, the amortized cost of an operation is O(1)

	* Potential method
		* one account for the whole structure 
		* account called potential 
		* a function 
			* maps a state (data structure) to a number $\phi(D_i)$
			*  $\hat{c}_i = c_i + \phi(D_i) - \phi(D_{i-1})$
		* main step: define potential function
			* Requirement: $\phi(D_n)-\phi(D_0)\geq0$
		* once $\phi$ is found amortised cost can be computed

* dynamic tables
	* table that contract and expands
		* expand: insert when full
		* contract: delete when too much free space
	* but needs to be relocated
		* allocate new space
		* copy elements
		* free old space

	* requirements
		* num - nember of elements
		* size - max number of elements
		* load factor: $\alpha$ = num/size
	* properties
		* amortised cost = constant 
		* load factor always above a constant (unless close to empty)


	*  expand with a constant 
		* naively and does not satisfied second requirement 

	* right way: expand by doubling 
		* need to
			* Pay $1 for inserting the element
			* Put $1 into element's account for reallocating it later
			* Put $1 into the account of another element to pay for a later relocation of that element![[Pasted image 20230603165312.png]]
		* insertions < 3n amortised cost

	* deletions?
		* problem: avoid re-allocating without having "the money"
		* Delay contraction!
			* when num = size/4
			* 2. requirement satisfied $\alpha \geq 1/4$
