# What is data privacy?
- shearing data with an entity 
- data protection
	* protection of private data GDPR
		* general data protection regulation
	* data protection is what data privacy is in EU

different classes
* anonymeisation
* formal privacy models
* semantic security (will not be covered)

## what is the difference between data privacy and security
* data security focuses on systems in place that prevent malicious external attempts to access, steal, or destory data
* data privacy focuses on the ethical and legal use and access to sensitive data and PII

# Data anonymeisation
* remove "personally identifying information" PII
* problem: PII has no technical meaning
	* defined in disclosure notification laws
	* in privacy breaches, any information can be personally identifying 

* formalise a model
![[Pasted image 20230501125007.png]]

![[Pasted image 20230501125129.png]]

should one remove quasi-identifiers?
* remove key attr since it is private
* and want to look at sentitive attr
* but make the quasi-identifiers more general not to make it less likely to match people
	* like make it birth year instead
![[Pasted image 20230501125415.png]]

* K-anonymity Intution
	* It protects the individuals from attacks to quasi-identifiers
	* The information for each person contained in the released table cannot be distinguished from at least k-1 individuals whose information also appears in the release
		* Example: you try to identify Bob in the released table, but the only information you have is his birth date and gender. There are other k-1 men in the table with the same birth date and gender.
	* Any quasi-identifier present in the released table must appear in at least k records

* K-anonymity definition
![[Pasted image 20230501125630.png]]![[Pasted image 20230501125648.png]]

* achieving k-anonymity
	* generalisation
		* suppress the low significant bits, like remove dates and only keep years 
		* ranges like age 20-25
		* Generalisation lattice
			* A lattice describing the possible strategies to achieve kanonimity
			* A directed acyclic graph
			* example:![[Pasted image 20230501130303.png]]
		* utility
			* Each generalisation step introduces information loss – error
			* The larger the equivalence class, the larger the error
			* We need strategies to decide how to generalise
				* Minimum distance: select the generalisation(s) with the lowest number of generalisation steps
				* Maximum distribution: select the generalisation(s) with the maximum number of distinct tuples
				* Minimum suppression: select the generalisation(s) with the minimum information loss



