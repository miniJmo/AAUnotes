* hvad er extreme programming (XP)? 
	* Det er en iterativ agil metode,
	* XP har fokus på samarbejde, hurtigt brugbar software, og skillful udviklings praktikker 

* hvorfor er xp ekstremt?
	* hvis code review er godt, så skal det gøres hele tiden
	* hvis test er godt, så skal man hele tiden teste
	* generelt set hvis noget er godt, så skal det hele tiden gøres 
		* og hvis noget er dårligt så skal man ikke gøre det

* Hvilke værdier er XP baseret på ifølge Larman? 
	- *Kommunikation*: XP-programmører kommunikerer med deres kunder og andre programmører (mundtlig kommunikation for krav og design er meget vigtig) 
	- *Enkelhed*: Hold designet enkelt og rent 
	- *Feedback*: Feedback ved at teste deres software fra dag ét 
	- *Mod*: Lever systemet så tidligt som muligt og implementer ændringer som foreslået. XP er derfor i stand til modigt at reagere på skiftende krav og teknologi

* XP har en lang række praktikker for at være så effektive som muligt 
	- **Test-først-udvikling**: En automatiseret unit test framework bruges til at skrive test for et nyt stykke funktionalitet, før selve denne funktionalitet implementeres. 
	- **Refaktorering**: Alle udviklere forventes at refaktorisere koden løbende, så snart der er fundet mulige kodeforbedringer. 
		* Du bør næsten altid refaktorere, hvis du synes, en eller anden kode, der er virkelig dårlig (affalds-afhentnings-refaktor) 
	- **Parprogrammering**: Udviklere arbejder i par, tjekker hinandens arbejde og yder støtte til altid at gøre et godt stykke arbejde. 
	- **Kontinuerlig integration**: Så snart arbejdet med en opgave er afsluttet, integreres den i hele systemet. Efter enhver sådan integration skal alle unit test i systemet bestå. 
	- **Kunde på stedet**: En repræsentant for slutbrugeren af systemet (kunden) bør være tilgængelig på fuld tid til brug for XP-teamet. Kunden er medlem af udviklingsteamet og er ansvarlig for at bringe systemkrav til teamet til implementering.

* XP gør brug af noget der hedder user stories
* En en user story er et *kort*, uformel beskrivelse af en funktion eller et krav, som en kunde eller slutbruger ønsker i et softwareprodukt.  
* *Formålet* med en user story er at fange essensen af kravet og tjene som et løfte om en samtale mellem udviklingsteamet og (on-site) kunden.  
* Det er et udgangspunkt for diskussion og uddybning, frem for en detaljeret specifikation. 
* User stories er en letvægtig og fleksibel måde at fange krav på. 
	* `Som en [bruger], vil jeg have [en funktion], så det [gavner noget].`
	* `As a <user> I want <feature> so that <why>`

* Hvorfor er **TDD** godt: 
* *Testdrevet udvikling* (TDD) anses for at være en god praksis inden for softwareudvikling af flere grunde: 
	* *Sikkerhedsnet*: Ved at skrive automatiserede test, før du skriver nogen kode, giver TDD et sikkerhedsnet, der hjælper med at fange fejl og defekter tidligt i udviklingsprocessen. Dette giver udviklere mulighed for at fange og rette problemer, før de bliver et problem, og det er med til at sikre, at koden er af høj kvalitet. 
	* *Lave omkostninger ved defekter*: Ved at fange defekter tidligt hjælper TDD med at reducere omkostningerne ved defekter. Jo tidligere en defekt opdages, jo billigere er det at udbedre. Dette skyldes, at kodebasen er mindre og mindre kompleks, og koden er stadig frisk i udviklerens bevidsthed. 
	* *Gør altid små trin*: Ved at skrive test først, er udviklere tvunget til at tage små trin i deres udviklingsproces. Dette er med til at sikre, at koden er velstruktureret og let at forstå, og det er også med til at undgå over-engineering. 
	* *Mindre frygt for at ændre kode*: Fordi koden er gennemtestet, er udviklere mindre bange for at ændre den. Dette giver mulighed for mere fleksibilitet i udviklingsprocessen, og det er også med til at sikre, at koden kan vedligeholdes. 
	* *Bedre kodekvalitet*: Ved at bruge TDD er koden mere læsbar, vedligeholdelig og mindre tilbøjelig til fejl. Dette skyldes, at koden er skrevet til at opfylde specifikke krav, og den er grundigt testet, før den implementeres. Dette er med til at sikre, at koden er af høj kvalitet, og den er let at forstå, vedligeholde og ændre over tid. 
* Samlet set er TDD en praksis, der hjælper med at forbedre kodens kvalitet og øge udviklingshastigheden ved at fange defekter tidligt, det hjælper også med at øge udviklerens tillid til at ændre koden og det sikrer, at koden kan vedligeholdes og let at forstå.


* lifecycle af et system i xp er delt op i faser
	* udforskning
	* planlægning
	* iterationer til første release 
	* production
	* maintaining ![[Pasted image 20240112124846.png]]

