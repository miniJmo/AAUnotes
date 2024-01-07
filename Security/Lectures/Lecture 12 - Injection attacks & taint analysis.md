# Injection attacks

sannititaion handler om at fjerne alle de farlige tegn
validation er til at sørge for at input passer overens med hvad vi forventer

# Taint analysis
vi vil gerne sørge for at det tainted input ikke rammer et output



* tjek om ouput er tainted før at det outputtes
	* kast en exception
		* stort runtime cost (perl ting)

dynamisk 
![[Pasted image 20230508131741.png]]

statisk taint analyse 
![[Pasted image 20230508131755.png]]
![[Pasted image 20230508132048.png]]
