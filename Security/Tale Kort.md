# Access Control Models
* var en af de første måder at formalisere sikkerhed på
* er omkring: hvilke Subjekter har adgang til hvilke Objekter igennem hvilke Actions 
	* subjekt: brugere
	* Objekter: filer, DB
	* Actions: read, write 

* Kan formulerer som en matrice
	* rækker: capabilities af Subjekter
	* kolonner: Access control lister over Objekter

* Access?
	* to måde at give access
	* DAC: Discretionary
		* ejeren af objektet definere adgang og i hvilket omfang
	* MAC: Mandetory
		* lavet en access control policy over hele systemet 

* Policy
	* kan være en state machine af systemet
	* init state er sikkert, 
	* alle lovlige samt transitions 
	* Der er også tilføjes forskellige sikkerheds niveauer
		* lattice

* Bell-LaPadula model BLP
	* klassisk metode
	* state machine MLS policy
	* specifikation af fortrolighed
		* subjekt kun adgang til objekter på samme eller lavere niveau

	* består af states udfra tre sæt
		* B: nuværende adgang (for S til O igennem A)
		* M: sæt af access kontrol matricer
		* F: sikkerheds klassifikationer
			* max niveau 
			* nuværende niveau 
			* objekt niveau

	* Properties:
		* simple security: no read up
		* \* : no write down
		* Discretionary security: tillader S at udføre A på O, hvis S har rettigheden

	* sikkerhed:
		* state er sikkert hvis ss og \* er overholdt 
		* transition er sikker hvis begge states er sikre

	* kritik
		* System Z
			* løses med de-/re-classifier
		* side-channels
			* lægger info igennem observerbar effekt
			* løses med secure information flow
		* ikke særlig fleksible 
			* svært at dele information imellem lag




