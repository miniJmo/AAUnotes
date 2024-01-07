
# Configuration management
* … is concerned with the policies, processes, and tools for managing changing software systems.
* **Configuration**: “a collection of specific versions of hardware, firmware, or software items combined according to specific build procedures to serve a particular purpose”

* Der er fire hoved begreber inden for CM
	1. **Change management**
	1. **Version management**
	2. **System building**
	3. **Release management**

## Change management
* *change is inevitable* 
1. hold øje med forslag til ændringer til software'en fra kunden/udvikleren
2. beregn prisen og gavnligheden af ændringen 
3. bestem om og hvornår ændringerne skal tilføjes

* Changes are managed by a Change Control Board (CCB) or product development group![[Pasted image 20231101082730.png]]

## Version Control
![[Pasted image 20231101083132.png]]
* Der er to måder at håndtere den her problem stilling på
	* pessimistisk: file locking
	* optimistisk: version merging 

* forståelsen af version kontrol med forskellige codelines & baselines![[Pasted image 20231101083641.png]]

* branching:![[Pasted image 20231101083707.png]]

* Configuration Management terminology (Differs from Git)
	* *Baseline*
		* A baseline is a collection of component versions that make up a system. Baselines are controlled, which means that the versions of the components making up the system cannot be changed. This means that it is always possible to recreate a baseline from its constituent components
	* *Branching*
		* The creation of a new codeline from a version in an existing codeline. The new codeline and the existing codeline may then develop independently.
	* *Codeline*
		* A codeline is a set of versions of a software component and other configuration items on which that component depends.
	* *Configuration (version) control*
		* The process of ensuring that versions of systems and components are recorded and maintained so that changes are managed and all versions of components are identified and stored for the lifetime of the system.
	* *Configuration item or software configuration item (SCI)*
		* Anything associated with a software project (design, code, test data, document, etc.) that has been placed under configuration control. There are often different versions of a configuration item. Configuration items have a unique name
	* *Mainline*
		* A sequence of baselines representing different versions of a system.
	* *Merging*
		* The creation of a new version of a software component by merging separate versions in different codelines. These codelines may have been created by a previous branch of one of the codelines involved.
	* *Release*
		* A version of a system that has been released to customers (or other users in an organization) for use.
	* *Repository*
		* A shared database of versions of software components and metainformation about changes to these components.
	* *System building*
		* The creation of an executable system version by compiling and linking the appropriate versions of the components and libraries making up the system.
	* *Version*
		* An instance of a configuration item that differs, in some way, from other instances of that item. Versions always have a unique identifier
	* *Workspace*
		* A private work area where software can be modified without affecting other developers who may be using or modifying that software.


* Version control (VC) systems identify, store and control access to the different versions of components. There are two types of modern version control system
	* Centralized systems, where there is a single master repository that maintains all versions of the software components that are being developed. *Subversion* is a widely used example of a centralized VC system.![[Pasted image 20231101090338.png]]
	* Distributed systems, where multiple versions of the component repository exist at the same time. *Git* is a widely-used example of a distributed VC system.![[Pasted image 20231101090352.png]]

* It provides a backup mechanism for the repository. 
	* If the repository is corrupted, work can continue, and the project repository can be restored from local copies. 
* It allows for off-line working so that developers can commit changes if they do not have a network connection. 
* Project support is the default way of working. 
	* Developers can compile and test the entire system on their local machines and test the changes that they have made.

## System Building 
* Building a large system is computationally expensive and may take several hours Hundreds of files may be involved System building tools may provide:
	* a dependency specification language and interpreter
	* tool selection and instantiation support
	* distributed compilation
	![[Pasted image 20231101090656.png]]

* man kan bruge Scons eller Jenkins CI

* Continuous Integration![[Pasted image 20231101090810.png]]

* The development organization sets a delivery time (say 2 p.m.) for system components.
	* If developers have new versions of the components that they are writing, they must deliver them by that time.
	* A new version of the system is built from these components by compiling and linking them to form a complete system.
	* This system is then delivered to the testing team, which carries out a set of predefined system tests
	* Faults that are discovered during system testing are documented and returned to the system developers. They repair these faults in a subsequent version of the component.

## Release Management 
… A system release is a version of a software system that is distributed to customers.

1. The release must be documented to ensure that it can be re-created
2. A release Baseline is that documentation. It includes all versions of codefiles, libraries, documentation as it was when the release was created
NOTE: This is the definition of ”baseline” in context of configuration management. The word baseline is used in many other context, baseline cost in project planning. GIT also uses the term baseline for something else.

# Plan driven vs Agile CM
![[Pasted image 20231101091736.png]]

# DevOps
![[Pasted image 20231101091819.png]]
* vi har et krav og det skal så hurtigt ud til kunden (automatisering)
![[Pasted image 20231101091842.png]]

## Lean software development 
* **Seven principles**
	* Optimise the whole
	* Eliminate waste
	* build quality in
	* Learn constantly 
	* Deliver fast
	* Engage everyone, and
	* Keep getting better
![[Pasted image 20231101092039.png]]
