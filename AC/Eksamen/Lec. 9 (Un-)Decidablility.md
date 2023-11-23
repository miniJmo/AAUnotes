
# Universal Turing machines (UTM)
Decision Problems:
* Acceptance: Does a given string belong to a given language
* Emptiness: Is a given language empty?
* Equality: Are given two languages equal?

These problems only makes sense how the different languages are described 

|     | Acceptance | Emptiness | Equality |
|-----|------------|-----------|----------|
| DFA | ?          | ?         | ?        |
| NFA | ?          | ?         | ?        |
| CFG | ?          | ?         | ?        |
| TM  | ?          | ?         | ?        |

Universal Turing Machine:
* Given a TM $\langle M \rangle$ and a string $w$, does $M$ accept $w$?![[Pasted image 20230604101507.png]]


# Diagonalisation
* Claim: There are some languages that are not recognisable (and therefore not decidable).
	* proof:
		* Each TM M has exactly one language L(M)
		* so let's count
			* how many TMs are there? $\infty$
			* how many languages are there? $\infty$
		* dead end?

no since different sets can have the same size even though they dont have the same symbols

## Bijection
what about $\mathbb{Z}$ vs $\mathbb{N}$? (integers vs natural numbers)
* well one can count, but...
* can also use Bijection:
	* Two sets are of the the same size iff there is a bijection btween them
	* Definition:
		* A function $f: A \rightarrow B$ is called bijection (correspondence) iff
			* $f$ is injective (one-to-one), $f(a) \neq f(b)$ whenever $a\neq b$, and
			* $f$ is surjective (onto), for every $b \in B$ there is $a\in A$ such that $f(a)=b$.

### Bijection example
![[Pasted image 20230604103315.png]]
Note: the naive way of thinking of mapping each natural number to itself does not work because then negative numbers are not mapped to any natural number.![[Pasted image 20230604103438.png]]

rational numbers $\mathbb{Q}$:
![[Pasted image 20230604103504.png]]

## Countable sets
definition:
* A set $A$ is countable if it it either finite or there is a bijection between the set $A$ and the set of natural numbers.

facts: 
* all even natural numbers are countable 
* The set of integer numbers are countable 
* The set of rational numbers are countable 

Theorem: 
* The set of real numbers are countable 
proof by contradiction via the diagonalisation method.

![[Pasted image 20230604104231.png]]

## Diagonalisation 
![[Pasted image 20230604104507.png]]

Theorem:
* The set of all TMs is countable.
proof sketch: 
* Diagonalisation on $w_i \in L_j$ for languages $L_j$ and words $w_i$ ![[Pasted image 20230604110013.png]]
corollary: There are some languages that are not recognisable 


# Decidable Problems
Decision problems make sense only if we specify how the given languages are described (they must have a finite description e.g. via finite automata, cfg or TMs).

|     | Acceptance | Emptiness | Equality |
|-----|------------|-----------|----------|
| DFA | **yes**          | ?         | ?        |
| NFA | ?          | ?         | ?        |
| CFG | ?          | ?         | ?        |
| TM  | ?          | ?         | ?        |

## acceptance
problem: Given a DFA B and a string w, does B accept w?![[Pasted image 20230604110600.png]]

problem: Given a NFA B and string w, does B accept w?![[Pasted image 20230604110737.png]]


## Summary 
8 out of 12 options are decidable: (can see the proofs in slides )

|     | Acceptance | Emptiness | Equality |
|-----|------------|-----------|----------|
| DFA | yes          | yes         | yes        |
| NFA | yes          | yes         | yes       |
| CFG | yes          | yes         | **no**        |
| TM  | **no**          | **no**         | **no**        |


# An Undecidable Problem
acceptance problem for a Turing machine: Given a TM M and a string w, does M accept w?
![[Pasted image 20230604111420.png]]
Theorem:
* The language $A_{TM}$ is undecidable 
* The language $A_{TM}$ is recognisable 
proof of recognisable:
* construct a recogniser U for $A_{TM}$
	* U = ”On input ⟨M, w⟩:
	* 1. simulate M on w.
	* 2. if M accepted then U accepts (same for reject)
Remark: The machine U (also called the universal TM) is not a decider (if M runs into an infinite loop on input w, then U runs into an infinite loop on input ⟨M, w⟩).

proof of Undecidability:
* By contradiction assume that there is a decider H for $A_{TM}$:![[Pasted image 20230604112352.png]]
* From H we can build a machine D, which is also a decider:![[Pasted image 20230604112427.png]]
* What happens if we run D on $\langle D \rangle$?
	* D accepts ⟨D⟩, but then H rejected ⟨D,⟨D⟩⟩ and hence D did not accept ⟨D⟩, contradiction!
	* D rejects ⟨D⟩, but then H accepted ⟨D,⟨D⟩⟩ and hence D accepted ⟨D⟩, contradiction! 
* So D cannot exist, so H cannot exist either 

Diagonalisation and $A_{TM}$![[Pasted image 20230604112819.png]]


# Co-recognisable Languages
Intuition for a recognisable language L (recognised by TM M):
* If $w \in L$ then M run on w will halt in accept state
* If $w \notin L$ then M run on w will reject or loop.

Intuition for a co-recognisable language L (recognised by TM M):
* If $w \notin L$ then M run on w will halt in accept state
* If $w \in L$ then M run on w will reject or loop.

Theorem: 
* A language $L$ is co-recognisable if $\bar{L}$ is recognisable. ![[Pasted image 20230604115104.png]]
Theorem:
*  A language is decidable iff it is recognisable and co-recognisable ![[Pasted image 20230604114841.png]]
