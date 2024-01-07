# Fuzz Test
* fuzz testing gætter

* test er dyrt og tager tid
* fuzz testing prøver at lave automatisk unit test
![[Pasted image 20230424124310.png]]

* det er ekstremt dumt og ekstremt trivielt 
	* men det virker

## blackbox fuzzing 
* observere input og output, men vi ved ikke hvad der sker der imellem 
	* problem: det er tilfældigt, så hvor lang tid tager det
		* det kan køre uendelig lang tid

metoden er dum men det behøver vi ikke at være aka.
![[Pasted image 20230424125229.png]]

Det virker, men det beviser ikke noget hvis den ikke crasher. For det sikre ikke at vi har ramt noget som kunde udløse et crash siden at det er en "blackbox"

hvis man ser på output, kan man måske se hvor langt man er i at finde noget spændende i koden fx
![[Pasted image 20230424125851.png]]

### mutation
med mutation kan man måske komme tættere på det spændende kode
![[Pasted image 20230424130341.png]]

ideer til mutation test
![[Pasted image 20230424125944.png]]
![[Pasted image 20230424130143.png]]

### generation based

![[Pasted image 20230424130541.png]]


![[Pasted image 20230424130717.png]]

* fuzzing harness: det er hvor meget kode og tid vi skal bruge til lave fuzzing 

this is great to play with fuzzing 101: github.com/larsbpf/fuzzing-lecture


### whitebox & greybox
![[Pasted image 20230424141136.png]]


![[Pasted image 20230424141354.png]]
* directed = når man leder efter et bestemt stykke kode
* coverage = prøver at finde så meget som muligt

* instrumental 
![[Pasted image 20230424141542.png]]

### AFL generelt 
![[Pasted image 20230424141757.png]]

## Assertion & Exposing 
* kigger efter bugs og ikke kun crash
![[Pasted image 20230424142307.png]]


## whitebox fuzzing
vi har og ved alting
![[Pasted image 20230424150834.png]]
![[Pasted image 20230424150849.png]]
