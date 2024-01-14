* test er helt bassalt forskellige metoder der understøtter verifikation og validering
	* ved at vise om programmet gør hvad det er meningen at den skal gøre
		* og finde de fejl der nu måtte være

* nøgle aktiviterne i testing er 
	* først at vise/demonstrere at softwaren imødekommer kravene
	* og så finde inputs til programmet der gør at det opfører sig uhensigtsmæssigt
		* fx sql injection og andet 

* testing hænger meget sammen med kvalitets kontrol (quality management)
	* da tests hænger meget sammen med verifikation og validering 
		* da man verificere med unit test for at tjekke om korrekthed af programmet
		* validering sker så ved user acceptance test og prototyper

* testing er delt op i flere stadier 
	* først er der udviklings test
		* med unit tests, component tests og system tests
	* derefter er der release testing
		* hvor man laver requirement testing, scenario testing (good enough for use), samt performance testing
	* til sidst er der så user testing
		* er programmet egnet til formålet? acceptance (testing)

* testing i en plandrevet proces versus en agil proces er lidt forskelligt 
	* i den plandrevet der er test en separat fase hvor man evt tager brug af et QA team
		* det er en meget slavisk til gang, 
		* først så designer man test cases, 
		* derefter finder man på noget test data der måske vil have mulighed for at ødelægge programmet.
		* for så at køre programmet med det her test data for at se hvilke resultater man får og sammenlign dem med test case'ene ![[Pasted image 20240114161719.png]]
	* den agile måde at gøre det på er lidt anderledes 
		* i agile metoder så sker test hele tiden (gerne TDD)
		* hvor det er teamet selv der laver testene og sætter dem op
		* agil testing er så vidt muligt automatisk, da manuelle test tager lang tid at lave og tager lang tid at så svar. 
		
	* for at gå videre så kan vi tale om den agile test kvadrant 
		* der viser hvordan man agilt kategorisere forskellige tests
		* den er sat op i to akser
			* business vs technology 
			* og supporting the team vs critiquing product 
			* hvor q1 (support & tech) har man automatiseret tests så som unit og component tests. hjælper teamet med korrekthed
			* q2 (support & business) forstå hvad kunden ønsker, finder requirements
			* q3 (critique & business) test og fremvisning af færdige dele eller hele systemet til kunden
			* q4 (critique & tech) Systemet som helhed bliver testet, performance, sikkerhed og ellers “ility”-test som også hænger sammen med quality
			* ![[Pasted image 20240114163320.png]]

* TDD ![[Pasted image 20240114165803.png]]
