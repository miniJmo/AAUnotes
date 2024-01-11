* vandfald: ![[Pasted image 20231218190542.png]]
* Iterativ model: ![[Pasted image 20231218190624.png]]

* vandfald er en plandrevet software proces model, som har en række af faser man skal igennem
* først er der krav specifikationen, der hvor man får alle krav fra kunden 
* dernæst er design fasen hvor man designer hvordan systemet og softwaren skal sættes op
* så kommer selve implementations fasen hvor man udvikler selve produktet, hvor man også samtidig laver unit tests
* derefter så laver man så større system- og integrationstest 
* Til sidst er der så vedligeholdelses fasen hvor man sørger for at systemet kører og fikser bugs
	* hvis der er noget der skal ændres skal man først forbi vedligeholdelse fasen

* Den iterative model kan både være plan drevet og agil og fungere lidt anderledes end vandfald
* først starter man ud med en outline fra kunden om hvad de gerne vil have
* hvorpå man så begynder at udføre forskellige aktiviteter, hvilket sker sammenflættet
	* specificere hvad der skal laves
	* udvikle det
	* og så validere det
* det bliver man ved med indtil man laver en version af system (initial version)
	* får så feedback og går tilbage til aktiviteterne 
* laver en ny version, får mere feedback, tilbage til aktiviteterne. 
* sådan bliver man ved indtil man når til en endelig version, som er hvad kunden gerne vil have.

* Den iterative model kommer af at man sjælden kommer frem til en komplet problem løsning i første forsøg.
* det er også nemmere at gå tilbage når indser at man har lavet en fejl, samtidig er det også billigere og nemmere at rette software imens det bliver udviklet
* den iterative model har tre fordele over vandfald
	1. prisen af at med regne ændrede krav resultere i at der skal ændres mindre analyse og dokumentation ifht. vandfald
	2. nemmere at få kunde feedback af det udviklingsarbejde der er lavet. kunder kan nemmere kommentere på demo'er end software design dokumenter.
	3. mulighed for hurtigere levering og udvikling af brugbar software til kunden. Selvom ikke alt funktionaliteten er da kan kunden stadig få gavn af softwaren hurtigere en vandfald

* Dog er den iterative model ikke altid den bedste
	* fx hvis kunden har mange bureaukratiske processer
	* processen er ikke synlig. Managers har brug for regulære leverancer for at kunne måle fremgangen. det er ikke kost effektivt at lave dokumentation for hver iteration hvis udviklingen sker hurtigt.
	* system strukturen har en tendes til at bryde lidt sammen når der kommer nye iterationer, medmindre at der bliver brugt penge og tid på refaktorering.
		* man bør næsten altid refaktor hvis man ser dårlig kode.

* hvornår bør man bruge den iterative vs vandfald(Boehm: homeground)
	* udefineret løsning: iterative (agil)
	* veldefineret løsning: vandfald (plandrevet)
