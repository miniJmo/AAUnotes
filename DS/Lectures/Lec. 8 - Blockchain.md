# Crypto tools
* cryptographic hash function
	* H: X = {0,1}* -> Y = {0,1}$^L$
		* with L fixed
			* Examples for L: 128/160/256/512 bits

		* Informal property:
			* a small change in the input produces a completely different output

		* Security properties (collisions exist, but are hard to find):
			* Pre-image resistance: ∀ 𝑦 ∈ 𝑌, it is hard to find 𝑥 ∈ 𝑋 such that H(x) = y
			* Second pre-image resistance: given a particular 𝑀 ∈ 𝑋 and thus h = 𝐻(𝑀), it is hard to find 𝑀′ with H(M′) = h
			* Collision-resistance: it is hard to find 𝑥1 ∈ 𝑋 and 𝑥2 ∈ 𝑋, with 𝑥1 ≠ 𝑥2 and 𝐻(𝑥1) = 𝐻(𝑥2)

![[Pasted image 20231026125100.png]]
![[Pasted image 20231026125838.png]]
![[Pasted image 20231026125855.png]]
![[Pasted image 20231026125904.png]]

* SHA: Secure Hash Algorithm
	* The Secure Hash Algorithm is a family of cryptographic hash functions published by the National Institute of Standards and Technology (NIST) as a U.S. Federal Information Processing Standard (FIPS)![[Pasted image 20231026125946.png]]

* Using Hashes![[Pasted image 20231026130411.png]]

* It is also possible to chain hashes in chunks 
	* Let’s split data in chunks $c_1 \dots c_k$
	* I compute the hashes $h_1 = H(c_1), h_2 = H(C_2||h_1)\dots h_k = H(c_k||h_{k-1})$
	* From time to time, you can ask me a hash, for example $ℎ_{10}$ to verify the first 10 chunks (blocks). Later on, you ask me $ℎ_{20}$ to verify the chunks 11 to 20


* for digital signatures there are three algorithms ![[Pasted image 20231026131038.png]]

## Merkle Tree
* is a tree of hashes
	* a data structure summarizing information about a big quantity of data with the goal to check the content
	* Main ingredient: a *complete binary tree* built starting from an initial set of symbols

![[Pasted image 20231026132309.png]]






# Blockchain basics
* A distributed database that is used to maintain a continuously growing list of records, called blocks. Each block contains a timestamp and a link to a previous block![[Pasted image 20231026133057.png]]

* hash pointer
	* point to some info
	* the info is hashed 
* with a hash point we can
	* ask to get the info back
	* verify that it hasn't changed 

* Tamper-evident data pointer = hash pointer![[Pasted image 20231026133311.png]]


# Blockchain details



# Ethereum smart contracts