A language being decidable, does not mean that we can realistically solve it.
* It can require too much resources (time, memory).

Complexity theory aims to make a general conclusion about time and space requirements of decidable problems.

From now on we only consider deciders and decidable languages.

# Algorithm Complexity 
how do we measure time and memory?
* Time = number of computational steps
* Memory = the number of used tape cells
we will only focus on time and asymptotic worst-case behaviour of programs

## Runtime of a TM
Definition:
* Let M be a deterministic decider. The running time or worst-case time complexity of M is a function $f: \mathbb{N} \rightarrow \mathbb{N}$
* where $f(n)$ is the maximum number of steps that M performs on any input of length n.

from now on n always denotes the length of the input string.

### Big-O Notation 
Asymptotic upper bound definition:
* Let $f,g:\mathbb{N} \rightarrow \mathbb{R}^{>0}$ be functions. We write $f(n) = \mathcal{O}(g(n))$ iff
	* there are positive integers $c$ and $n_0$ such that
	* $f(n) \leq c \cdot g(n)$ for every $n \geq n_0$ 
![[Pasted image 20230604153648.png]]
![[Pasted image 20230604153706.png]]


# Complexity classes
Focus of Algorithm Complexity: 
* Study of concrete algorithms and the analysis of their precise complexity 

Focus of Complexity Theory: 
* Study of problems (languages) rather than concrete algorithms 
* Can we say for a given problem how easy/hard is it to solve?

Complexity Class definition:
* A complexity call is a set of computational problems of related resource-based complexity 

Complexity Class TIME definition:
* Let $t:\mathbb{N} \rightarrow \mathbb{R}^{>0}$ be a function.![[Pasted image 20230604154531.png]]

* In other words: TIME(t(n)) is the class (collection) og languages that are decidable by TMs running in time $\mathcal{O}(t(n))$.
* Fact: $TIME(n) \subset TIME(n^2) \subset \cdots \subseteq \cdots$
	* ![[Pasted image 20230604154820.png]]

Theorem:
* For any time constructible funciton $t: \mathcal{N} \rightarrow \mathcal{N}$, a language A exists that is decidable in  $\mathcal{O}(t(n))$ time but not decidable in time $o(\frac{t(n)}{\log(n)})$.
proof sketch: We construct a language that can be decided in O(t(n)) but that cannot be decided in time $o(\frac{t(n)}{\log(n)})$, by making sure it differs from all languages decidable in that time (using diagonalization). 
→Giving more time to a TM, means that we can solve more problems

example:![[Pasted image 20230604155917.png]]

### Relationships between k-tapes and single-tape TMs
Theorem:
* Let t(n) be a function s.t. t(n) $\geq$ n.
* every k-tape TM running in time t(n) has an equivalent single-tape TM running in time $\mathcal{O}(t^2(n))$
proof:
* Use the simulation of multi-tape TM M by a single TM M' (c.f. Chapter 8) and analyse the running time of M'.
![[Pasted image 20230604160758.png]]

![[Pasted image 20230604161310.png]]


# The Class P
Class P definition:
* The class P is the class of languages decidable in polynomial time on deterministic single-tape Turing machine, i.e.,
* ![[Pasted image 20230604161527.png]]

How to show that a language/problem $L_P$ is in P?
Provide a TM M such that:
* $L(M) = L_P$
* $M$ is a polynomial time decider

example of language in P:
![[Pasted image 20230604162509.png]]

encoding the input:
* When encoding numbers, we use a binary encoding (or any other encoding with base at least 2)but not the unary encoding.
	* example: ![[Pasted image 20230604163008.png]]![[Pasted image 20230604163824.png]]


## combining polynomials
![[Pasted image 20230604164208.png]]

## Other problems in P
![[Pasted image 20230604164332.png]]

## Closure Properties of P
Theorem:
* The class P is closed under intersection, union, complement, concatenation and Kleene start.

In other words:
* if $L_1$ and $L_2$ are decidable in deterministic polynomial time, then $L_1 \cap L_2$, $L_1 \cup L_2$, $\bar{L_1}$, $L_1.L_2$ and $L_1^*$ are decidable in  deterministic polynomial time too.![[Pasted image 20230604164700.png]]

EXPTIME:![[Pasted image 20230604164725.png]]

