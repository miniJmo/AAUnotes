Goals:
* to understand the external memory model and the principles of analysis of algorithms and data structures in this model
* to understand the algorithms of B-tree and its variants and to be able to analyse them
* to understand the main principles of external tree structures 
* to understand how the different versions of merge-sort derived algorithms work in external memory
* to understand why the amount of available main memory is an important parameter for the efficiency of external-memory algorithms 

modern hard drive specs:
* seek time: 4-10ms
* spindle speed: ~10K rpm => Half of ration: ~3ms
* transfer rate: 500 MB/s => Transferring 1 byte: 0.000003ms

# B-trees
* we are concerned only with keys
* the nodes have high fan-out(many children) = $\theta$(B)
	* Degree of a tree t:
		* Min_fan-out = t, Max_fan-out = 2\*t = B / index_entry_size
	* Root is the exception: can have as little as two children 
* B-tree is a balanced tree, and all leaves have the same depth: $h=\theta(log_tN) = \theta(log_BN)$![[

* internal nodes
	* t-1 to 2t-1 keys
	* pointer1 key1... pointerx keyx pointerx+1
	* key1 $\leq$ key2 ... $\leq$ keyx
	* pointer1.key $\leq$ key1 and keyx < pointerx+1.key
		* $key_{i-1} < pointer_i.key\leq key_i$

* pseudo code:
	* x is a node and x.n is the number of keys in the node
	* k is the key that we are searching for
	* x.keyi is the i-th key of node x; and x.ci is the i-th pointer of node x![[Pasted image 20230603105017.png]]

## B$^+$-trees 
* is a variant of B-trees
	* all data keys are in leaf nodes
	* leaf-nodes are connected into a doubly linked list
	* search is very similar to search in a binary search tree
		* always goes to a leaf
		* range searches are convenient 
		* cost: $\theta$(log$_B$N+k/B)![[Pasted image 20230603110219.png]]
* the algorithm
	* Down-phase. recursively traverse down and find the leaf (search)
	* Up-phase: insert the key. If necessary, split nodes and propagate the splits up the tree
* assumption:
	* In the down-phase pointer to traversed nodes are saved in the stack as there are no parent pointers

### Node splitting 
* leaf node: copy the middel key to the parent![[Pasted image 20230603111030.png]]
* Internal node: move the middel key to the parent, as in B-tree![[Pasted image 20230603111126.png]]
* The tree grows when the root is split into two nodes and their parent becomes the new root

### Example of insert in B$^+$-tree
* Insert P (maximum fan-out = 5 children = 4 data entries)
* Down-phase: Leaf node![[Pasted image 20230603111627.png]]
* need to split, since fan-out is 5, which means at most 4 keys in a node![[Pasted image 20230603111750.png]]
* cost: $\theta(\log_BN)$

#### more examples 
![[Pasted image 20230603113527.png]]
![[Pasted image 20230603113536.png]]


### Deletion 
* opposite of insertion:
	* phase 1: traverse down to find the key in a leaf
	* phase 2: remove the key and traverse up handling underfull nodes
		* underfull handling case: Distributed ![[Pasted image 20230603113905.png]]
		* case: merging ![[Pasted image 20230603113931.png]]

* R-tree and grow-post trees can be found on slide 25-26 in lec 4

# merge sort
![[Pasted image 20230605102121.png]]
![[Pasted image 20230605102220.png]]

* external memory sorting 
	* when data do not fit in main memory
	* rough idea: sort pieces that fit in main-memory and "merge" them
* merge sort: divide, conquer combine 

* Idea for external memory merge sort: increase the size of initial runs!
	* initial runs - the size of available main memory (M data elements)![[Pasted image 20230603115458.png]]

* Input file x, empty file y
* Phase 1: repeat until the end of file x:
	* read the next M elements from x
	* sort them in main memory 
	* write them at the end of file y
* phase 2: repeat while there is more than one run in y:
	* empty x
	* mergeAllRuns(y,x)
	* x is now called y, y is now called x

	* mergeAllRuns(y,x): repeat until the end of y
		* call twowayMerge to merge the next to runs from Y into one run, which is written at the end of X. 
		* twowayMerge: uses three main-memory arrays of size B:![[Pasted image 20230603120143.png]]
	* disk page size: B data elements
	* data file size: N elements, n = N/B disk pages
	* available main memory: M elements, m = M/B pages![[Pasted image 20230603120418.png]]
		* phase 1: read file x write file y: 2n = $\theta$(n) I/Os
		* phase 2: 
			* one iteration: read file y, write file x: 2n = $\theta$(n) I/Os
			* number of iterations: $\log_2N/M = \log_2n/m$
total run time: $\theta(n\log_2n/m)$

## multiway merge sort
* idea: merge all runs at once
	* phase 1: the same (do internal sorts)
	* phase 2: perform MultiwayMerge(y,x)![[Pasted image 20230603120926.png]]

* multiway merging![[Pasted image 20230603121005.png]]
* total run time $\theta$(n)
* catch: can only be done files with a limited size
	* phase 2 can merge a maximum of m-1 runs
	* Which means: N/M $\leq$ m -1 (n/m $\leq$ m-1)
