* parallel algorithms 
	* allows for computing multiple operations at the same time
	* aka. parallel
		* spawning threads
	* favourable: use more computer power
		* time reduction 

* how do they work?
	*  three concepts 
		* work: running time on 1 processor
		* span: running time on $\infty$ processor
		* parallelism: work/span = average processors used
	* good alg = more parallelism 
		* decreasing span?

* Parallel merge sort
	* spawn first recursive call
		* then sync                     ![[Pasted image 20230824152125.png]]
	* works, but not that impressive 
	* problem
		* merge is serialised 

	* multi-thread Merge
		* merge subarray A, B to C
		* in A find middle element x
			* median (pivot point)
		* binary search on B 

		* merge into C
			* put x in C
			* recursively merge elements less than x
				* put on the left
			* same for elements greater
				* on the right![[Pasted image 20230829105549.png]]
		* better running time 