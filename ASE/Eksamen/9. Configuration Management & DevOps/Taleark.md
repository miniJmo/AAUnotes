* konfiguration 
	* konfiguration er en samling ad specifikke versioner af hardware, firmware eller software kombineret til specifikke building procedures to serve a particular purpose”

* CONFIG MANAGEMENT
	* CM er særligt godt til at håndtere konfigurationer og ændringer via politikker, processer og værktøjer. Nødvendigt for at holde styr på ændringer og inkorporeringer af komponentversioner.
	* Særligt brugbart til større teams, der måske arbejder fra flere lokationer, da det hjælper hele teamet til at have adgang til nødvendig data og information.

* configuration management handler om hvordan man 
	* *change management*: handler om hvordan kontrollere og koordinere ændringer i software (fra kunden/udvikler) og beregne ændrings pris og gavnligheden. til sidst skal det så bestemmes om og hvornår ændring skal tilføjes.
	* laver *version management/control*: altså hvordan man håndtere at  to eller flere personer arbejder på den samme fil
		* pessimistisk: file locking
		* optimistisk: version merging
	* *system building (tools)*: Dette er processen af at samle komponenterne, dataen og bibliotekerne, og så kompilere det hele ned til en .EXE fil   
	* *release management*: det er processen af planlægge og klaregøre et software release til brugerne  

* når det kommer hvordan man styre sin kode med flere udviklere i CM 
* så er der flere forskellige fagtermer så som
	* codelines
	* branches
	* merging 
	* baseline![[Pasted image 20231101083707.png]]
* branching
	* codelines
	* merge
	* rollback


* DEVOPS
	* DevOps springer ud fra Lean tanke gangen
		* Lean handler om hvor hurtigt man kan komme fra rå materialer til et færdig produkt kendt som lead time
		* og at den bedste måde at mindske lead time er ved at arbejde i små batches
	* DevOps handler om value streams og hvordan vi hurtigst og bedst går fra en ide til et færdigt produkt 
		* value streamen begynder når man prøver at tjekke noget ind i versions kontrollen og ender når feature'en er i produktion 
	* målet er at have testing og operations skal ske samtidig med design og udvikling, for at få et hurtigt flow og høj kvalitet.
		* dette fungere bedst med disse små batches

	* det ideelle for DevOps er at udviklere får hurtig og konstant feedback på det de laver.
		* for så at hurtigt kunne rette op på det selv. 
		* ved hele tiden at tilføje lidt kode til vores version kontrol og køre tests på det, så kan vi med stor sikkerhed sige at det vil virke i produktion. Og at fejl hurtigt kan blive fundet og rettet.![[Pasted image 20240116191703.png]]
	* DevOps arbejder ud fra noget der bliver kaldet The Three Ways
		* hvor først får man dannet et flow fra udvikling og over i produktion
		* for så dernæst få konstant feedback på det er blevet lavet 
			* hurtigere finde fejl og rettet dem inden de bliver katastrofiske 
		* til sidst er det så at begynde at bruge continuous learning 
			* hvor man hele tiden lære fra hinanden og lære af fejl og succeser  
			* så man undgår at lave de samme fejl og får hurtigere noget ud og får feedback på det![[Pasted image 20240116192852.png]]
