* external memory algorithms
	* little space in main memory 
	* working on large data

	* merge sort
		* sort the data that fits main memory 
		* increase size of initial runs
			* has size of main memory (M)![[Pasted image 20230806212847.png]]

		* running merge sort 
		* input file x, empty file y
			* phase 1: internal sorts (repeat till eof x)
				* read M elements from x
				* sort them in main memory 
				* write to y
			* phase 2: 
				* empty x
				* mergeAllRuns
				* x => y, y => x
			
				* mergeAllRuns: repeat till eof y
					* call twowayMerge
					* merging two runs and write to x![[Pasted image 20230603120143.png]]


		* two Phase multiway merge sort
		* merge all runs at once
			* Phase 1: the same (do internal sorts)
			* Phase 2: perform MultiwayMerge(y,x)![[Pasted image 20230603121005.png]]
			* runs in O(n)
			* but requires limited size

		* general multiway merge sort
		* a lot of data or small memory 
			* Phase 1: the same (do internal sorts)
			* phase 2: perform multiwayMerge
				* but done in iterations 
				* groups of m-1 runs
					* m = number of diskpages in main-memory![[Pasted image 20230808102807.png]]