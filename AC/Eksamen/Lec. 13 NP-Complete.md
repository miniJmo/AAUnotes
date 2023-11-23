
# NP-Complete

HP-hardness definition:
* A language B is NP-hard iff for every $A\in NP$ we have $A\leq_P B$.
	* B is as hard as all other problems in NP (and possibly harder)

Remark: B is not necessarily an NP problem (NP-hard $\nsubseteq$ NP)

NP-Completeness definition:
* A language B is NP-complete iff
	* $B \in NP$ (containment in NP), and
	* for every $A \in NP$ we have $A\leq_P B$(NP-hardness)

Theorem:
* If B is NP-complete and $B \in P$, then P = NP
proof: We know that  $A\leq_P B$ and $B \in P$ then $A \in P$

Theorem:
* If B is NP-complete,  $B\leq_P C$, and $C \in NP$, then C is NP-complete
proof: because $\leq_P$ is transitive ![[Pasted image 20230604205849.png]]

Consequence:
* If just one NP-complete problem can be solved in P then all other problems in NP will be solvable in P (hence P=NP). 
* If P $\neq$ NP then none of the NP-complete problems is solvable in deterministic polynomial time.


# Cook-Levin Theorem
The Cook-Levin Theorem:
* The language SAT is NP-complete.
proof: SAT is clearly in NP. We have to show that SAT is NP-hard:
* Every language $A\in NP$ is poly-time reducible to SAT
	* Let us assume any given $A \in NP$, so
	* there is a nondeterm. decider M for A running in time O($n^k$).
* our aim: For any input string w construct in polynomial time a boolean formula $\phi$ such that
	* M accepts w iff $\phi$ is satisfiable.

## Boolean formula Describing Table of configurations
![[Pasted image 20230604211056.png]]

* Assume a table of configuration when M is run on $w = w_1\dots w_n$. We will construct a formula $\phi$ such that M accepts $w$ iff $\phi \in SAT$.
	* ![[Pasted image 20230604211308.png]]
The set of variables contains: $x_{i,j,s}$
Where $1\leq i,j\leq n^k$ and $s \in C$ is a tape symbol or a control state.
Note: There are only polynomial many variables w.r.t. to n.

Intuition:
* Variable $x_{i,j,s}$ is true iff cell\[$i,j$\] contain the symbol s.

when looking at the configuration table we get: ![[Pasted image 20230604212243.png]]

$\phi_{cell}$ Definition:
* Every cell\[$i,j$\] contains exactly one symbol s.![[Pasted image 20230604212452.png]]
note: $\phi_{cell}$ is of polynomial size w.r.t. to n.

$\phi_{start}$ Definition:
* The first row contains the initial configuration $q_0w_1\dots w_n$.![[Pasted image 20230604212713.png]]
note: $\phi_{start}$ is of polynomial size w.r.t. to n.

$\phi_{accept}$ Definition:
* There is an accepting configuration in the table.![[Pasted image 20230604212844.png]]
note: $\phi_{accept}$ is of polynomial size w.r.t. to n.

$\phi_{move}$ Definition:
* Every window in the table is legal.![[Pasted image 20230604213016.png]]
note: $\phi_{move}$ is of polynomial size w.r.t. to n.

![[Pasted image 20230604213258.png]]


# Other NP-Complete Problems
To show that a problem B is NP-complete we show that:
* B is in NP 
	* By providing a nondeterministic TM that decides B in polynomial time or
	* By providing a TM that validates some certificate solution c for B in polynomial time.
* B is NP-hard
	* By choosing $A \in NP$-hard and showing $A \leq_P B$.
	* (A should actually be NP-complete because otherwise the reduction is not possible if B is in NP)

Theorem:
* If A is NP-complete, $A \leq_P B$, and $B \in NP$, then B is NP-complete.

list of all NP-complete problems in slides: 3SAT, Clique, vetex-cover, Hampath
look at them if needed.

On the importance of NP-complete problems
* it is a good idea to take a look at the list of NP-complete problems and familiarise yourself with a few of them
	* if you need to solve a similar problem, it may give you a hint that your problem is hard
	* if you want to prove that a problem is NP-hard, you can use any of the them for the reduction
	* Knowing the name of a problem can help you to find good algorithms for it

![[Pasted image 20230604215850.png]]


