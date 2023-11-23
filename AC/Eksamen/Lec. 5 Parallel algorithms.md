Goals:
* to understand the model of dynamic multi threading (fork-join parallelism)
* to understand work, span, and parallelism 
* to understand and be able to analyse the parallel merge sort algorithm

* standard Fibonacci has a running time of $\theta$(~1.618$^n$) aka. exponential ![[Pasted image 20230603122858.png]]

# multi threaded Fibonacci 
* if we run Fibonacci with two recursive calls in parallel, using nested parallelism![[Pasted image 20230603123213.png]]
* "running time" is: S(n) = max(S(n – 1), S(n – 2)) + 1 = S(n – 1) + 1, thus S(n) = $\theta$(n)

* there are three main concepts: 
	 * Work: the running time on a machine with one-processor (T1)
		* fib:  $\theta$(~1.618$^n$)
	* Span: the running time on a machine with infinite-processors (T$\infty$) 
		* fib:  $\theta$(n)
	* Parallelism: Work/Span - how many processors on average are used by the algorithm
		*  $\theta$(~1.618$^n$/n)

	* more formally:
		* Computation log / trace– a DAG of serial strands of instructions (vertices) and dependencies (edges) between them.
		* Work = the number of vertices in the computation log.
		* Span = the length of the longest path (critical path) in the computation log.

## example of computation DAG
* using an example of computing Fibonacci number of 4.![[Pasted image 20230603124751.png]]
* ![[Pasted image 20230603124802.png]]

* Edge(u,v) means that u must execute before v![[Pasted image 20230603124940.png]]
* light grey boxes are spawned procedures and dark grey are called procedures 
* Work: number of vertices, 17
* span: the length of the longest path (critical path), 8


## work and span law
* Notation
	* work: T1
	* Span: T$\infty$
	* multi threaded computation on P processors: Tp

* Work law: Tp $\geq$ T1 / P
	* an ideal parallel computer with P processors can do at most P units of work
* Span law: Tp $\geq$ T$\infty$
	* an ideal parallel computer with P processors cannot take less time than a machine with unlimited number of processors 

## Speedup, slackness
* when running on an actual system with P physical threads:
	* Slackness of a computation: Parallelism / P
		* If slackness < 1 we can never achieve a perfect speed up.
	* Speedup = T1/Tp
		* perfect linear speedup, when speedup = P
![[Pasted image 20230603140211.png]]

## Computing Span
* sequential execution:
	* work and span: T(A) + T(B)![[Pasted image 20230603140327.png]]
* parallel execution:
	* work: T1(A) + T1(B)
	* span: max(T$\infty$(A), T$\infty$(B))                                   ![[Pasted image 20230603140511.png]]

* Goal of the parallel algorithm design – increase parallelism. 
	* Usually achieved by decreasing span (remember, parallelism = W/S) 
	* It may pay off to slightly increase work, if span can be decreased significantly (in practice, relevant for highly parallel systems, such as supercomputers, but also GPUs)
	* 