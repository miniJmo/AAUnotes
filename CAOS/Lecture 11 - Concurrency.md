# Tråde
Hyper-threads != software threads
det er fysiske tråde
* mål:
	* udnytte super scalar processering: instruktionsstrømmen i et enkelt (uoptimeret) program udnytter ofte ikke al regnekraften
	* effektivisere multi-programmering og kontext-switch
* ulemper:
	* Cache-trashing
	* Performance gevinst afhænger af applikation
	* Stort strømforbrug ifht gevinst.

**dark silicon** er mængden af digitale kredsløb som ikke kan tændes (eller køre på fuld kraft) pga. termiske begrænsninger.

* **Concurrency**: afvikling sker samtidigt. Ved ikke om det (ønsker ikke at antage at) det er på en eller flere CPU-kerner.
* **Multi-programmeret**: samtidig afvikling på en kerne, fx vha timeslicing. Pseudo-parallelt.![[Pasted image 20230426083240.png]]

* **(Ægte) Parallelt**: afvikling sker på flere kerner/processorer
	* Speedup!
	* Øget kapacitet (antal ”running” processer)
* **Distribueret**: Beregning foregår på fysisk adskilte maskiner forbundet i netværk
	* bedre svartid: øget pålidelighed og tilgængelighed (replikering), speedup via parallelitet

## Parallelitet 
* implicit
	* Instruktions-nivue parallelitet: Næsten :) gratis for programør

* Explicit
	* Tråde, større indsats: Javathreads, posix threads ect.
	* annotationer: Open MP

* Flynn's taxonomi
![[Pasted image 20230426083826.png]]

**Dagens pub quiz**: Hvis det tager 9 måneder for én kvinde at fostre ét barn, hvor lang tid tager det så for 3 kvinder?
* pointe at der nogle ting man ikke kan speedup alting parallel vs sekventiel 
* Amdahl's lov

# Race-conditions
HEISENBUGS
	husk at bruge locks for at udgå dem


# Mutexes


# Opgaver




