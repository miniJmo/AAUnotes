# Video noter
lægge og tage værdier fra bufferen
![[Pasted image 20230502172323.png]]![[Pasted image 20230502172352.png]]

samafor
* en klassisk *synkroniserings- og mutex* mekanisme 
* er et objekt som indeholde ventelist
	* `sem_init` laver den og giver værdien
	* `sem_wait` blokkere hvis værdien <= 0, fratrækker værdien med 1 og blokkere tråden
	* `sem_post` øger værdien med 1, hvis afventende (blokerede) tråde, vækkes en
![[Pasted image 20230502175406.png]]

![[Pasted image 20230502175704.png]]

* Lad en semafor (empty) tælle antallet n af ledige pladser: lad n producenter passere
* Lad en semafor (full) tælle antallet m af brugte pladser: lad m konsumenter passerer
* m+n == MAX
![[Pasted image 20230502175846.png]]
![[Pasted image 20230502175855.png]]
skaber baglås deadlock

spissende filosoffer
![[Pasted image 20230502180140.png]]
* en løsning kræver:
	* ingen deadlock
	* alle spiser; ingen udsultes
	* høj grad af samtidighed
![[Pasted image 20230502180318.png]]
en løsning: men deadlock
![[Pasted image 20230502180358.png]]
![[Pasted image 20230502180513.png]]

en løsning kan være at gøre den ene venstre håndet ![[Pasted image 20230502180617.png]]

## deadlock 
* deadlock sker når der er opstået et cirkel blandt en mængde tråde hvor de hver venter på en ressourse, som fastholdes af en anden 
![[Pasted image 20230502180847.png]]
en cirkulær venten

Betingelser:
* **Mutual Exclusion**: Tråde kan kræve eksklusiv adgang til de ressourcer de skal bruge
* **Hold-and-wait**: En tråd kan holde fast i en tildelt ressource, mens den venter på adgang til flere. *(”Stykvis allokering”)*
* **No preemption**: Ressourcer kan ikke magtfuldt fratvinges de tråde som holder dem.
* **Circular wait**: Der findes en cirkulær kæde af tråde, således at hver tråd holder en eller flere ressourcer som efterspørges af næste tråd i kæden
![[Pasted image 20230502181158.png]]

**forbygge**: Man kan bryde en af de her betingelser for at fjerne deadlock  
**Undvige deadlock**: scheduler, ved at bruge information om hvilke ressourcer der findes, kender trådenes behov, og undviger de afviklings-sekvenser som potentielt leder til baglås
**Genopretning**: Detekter om deadlock er opstået og ryd op.


# Lektionen 
* semafor
	* den har en tæller værdi og en ventekø
	* har wait = tæller ned med en i tælleren og blokkering
	* post = atomisk optælling
	* mutex og signalering i samme type
![[Pasted image 20230503083233.png]]
* mutex lock
	* dækker over en status (åben/lukket) + ventekø
	* atomisk åben og luk

* condition var
	* en ventekø: pthread_cond_t cond;
	* med atomiske operationer: cond_wait, cond_signal, cond_broadcast
	* parres med en lock -"monitor" til kritisk region
![[Pasted image 20230503083246.png]]

* semafor og mutex lock/condition vars kan ikke blandes, enten semafor eller mutex og conditions ikke blande

![[Pasted image 20230503084123.png]]

* live lock is a thing

![[Pasted image 20230503091839.png]]