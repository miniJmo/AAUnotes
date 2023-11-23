* Software quality management is concerned with ensuring that developed software  systems are “fit for purpose.”
	* meet the needs of their users
	* perform efficiently
	* reliable 
	* delivered on time
	*  within budget

* quality assurance
	* definition of processes and standards that leads to high quality

* quality control
	* is the application of these processes to weed out products that are not of the required level of quality

Humphrey (Humphrey 1989), in his classic book on software management, suggests an outline structure for a quality plan. This outline includes the following: 
1. *Product introduction* A description of the product, its intended market, and the quality expectations for the product. 
2. *Product plans* The critical release dates and responsibilities for the product, along with plans for distribution and product servicing. 
3. *Process descriptions* The development and service processes and standards that should be used for product development and management. 
4. *Quality goals* The quality goals and plans for the product, including an identification and justification of critical product quality attributes. 
5. *Risks and risk management* The key risks that might affect product quality and the actions to be taken to address these risks

### Alka recap
* de havde taget det der stod i scrum guiden og træk det længere ud
* Der er mange processer 

# Software quality
* objective:
	* Have been introduced to the quality management process and know why quality planning is important

* quality can be
	* excellence - Er det perfekt og det bedste
	* value - for man noget for pengene 
	* conformance 
	* expectation - leverede man det man ville have eller lidt mere end man regnede med

* It is hard to say when software meets its specification 
	* it is difficult to write unambiguous requirements 
	* Specifications usually combine requirements from different stakeholders
	* impossible to measure certain quality characteristics (fx maintainability)

* it is subjective process
	* QM team uses their judgement and maybe these questions to see if it is fit for use
		1. Has it been properbly tested and all requirements implemented?
		2. is it dependable to be put into use?
		3. performance good enough for normal use?
		4. is it usable?
		5. well structured and understandable?
		6. have standards been followed in the development?

* Quality is a reflection of one or more peoples’ assessment of correspondance between their expectations and experience of a product or service

* quality can be divided into three types
	* product
	* process
	* expectation 

	* these 3 types of quality drive a mix of expectations to
		* functionality often described with functional requirements/userstories 
		* non-functional requirements often called software quality attributes ![[Pasted image 20231018091553.png]]
			* but cant have them all ![[Pasted image 20231018091835.png]]
		* how the product is created or product quality is ensured (process)



# Quality management and agile development 
* Objective:
	* Understand how quality management in agile methods is based on the development of a team quality culture

* QM consists of
	* quality assurance
		* definition of processes and standards that leads to high quality
		* plan or design processes to prevent bad quality
		
	* quality control
		* is the application of these processes to weed out products that are not of the required level of quality
		* Monitor that work products meet quality standards

## cost of quality management 
* preventive costs
	* better planning
	* measurable quality factors (response time, load)
	* education and training of developers (in test, review)

* monitor costs
	* evaluation, peer review, code inspection
	* testing 
![[Pasted image 20231018093259.png]]

* Low quality (low quality management) is initially cheap, but becomes gradually more expensive
* High quality management, has an initial cost when quality processes are defined, but is cheaper later because users are reporting much less errors, and the code is more stable
* Quality management should be balanced to the cost – a process that is 100% defect free is very expensive, while decreasing quality management, will increase the amount of defects reported over time.
* We plan and design, how and when to do verification and validation in our process

## Quality assurance: quality of product and expectations 
* validation 
	* are we building a system that is fit for use
	* conforms to customers' expectations and experience 

* verification
	* are we building the system with all requirements implemented
	* conforms to requirement specification 

* techniques 
	* In general the techniques are
		*  Testing of programs and prototypes 
		* Reviewing of specifications, documentation and programs 
	* Is it verification or validation? 
		* for a test or review to be validation a user must participate, since they know if something is “fit for use”. 
		* a verification activity will focus on compliance to specification, and typically a user and customer do not participate.

## Quality management and agile development
**Informal** rather than document-based by establishing a **quality culture** where all team members are responsible for software quality through **agile quality practices**: 

* *Definition of Done*: Team agrees on criteria for a task to be complete 
* *Sprint review*: PO and other stakeholders validate the sprint delivery meets expectations 
* *Check before check-in*: Developers are responsible for organizing their own code reviews with other team members before the code is checked into the build system. 
* *Never break the build*: Team members should not cause the system to fail by testing their code changes against the whole system before check-in. 
* *Fix problems when you see them*: If a programmer discovers problems or obscurities in code developed by someone else, they can fix these directly rather than referring them back to the original developer.

# Software measurement 
* objective:
	* Understand how measurement may be helpful in assessing some software quality attributes, the notion of software analytics