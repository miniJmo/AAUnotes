# Web Security Attacks 
* Security was an afterthought → when used for critical infrastructure, we started worrying.
* OWASP top 10
* https://cheatsheetseries.owasp.org/

* What's the biggest Security concern → Cost-benefit of what to worry about aka bang for your buck
	 * OWASP top 10: the biggest concerns 

* OWASP is good for looking up how to prevent attacks and the specifics  

### Broken Access Control
* elevating your privileges 
* bypassing the access control
* fix: access control aka. only give privileges to users that need them

### Cryptograhic failures
* forgetting to encrypt data aka. sending clear text
* forgetting to update the encryption to the new standard
* using a randomness with a low seed aka low entropy 


## Injection Attacks
* SQL injections: dropping tabels 
* Looking in the database (getting Salts, Hash, ect.)
* running a command 
* escape SQL statement string to add your own SQL statement (to inject)
* Prepared statements are a better way
* Stored procedures are good. stored code on the database

### Command Injection
* fx Python function eval()
* avoid using eval()
* Anytime scripting thing
* Use an API to interact with the host system
* escape your user data
* use parameterised commands
* Run code in low-privileges environment



## Session Attacks
* Firesheep
* ![[Pasted image 20230327142747.png]]
	* preventable with HttpOnly
	* use secure flag on cookies

### Session fixation attack
* if the application the user allows the user to set the session id or named after the user (hased username)
* guess the hash-function and then it is easy to find the hash value for a username
* they can control your session
* avoid it by making the session ID a random number


## Cross-Site Request Forgery

***needs to be moved? might be injection stuff***

* mDe her properties gør at BLP er god til at bevare fortrolighed, men den er også svær at bruge i praktisk da især star property'en gør at man ikke skrive noget der under ens niveau.
anaged to tweet some embedded JS
* should not be possible to embed a JS script  
* Samy (computer worm)
* Happens a lot
* three types: Reflected, Stored, DOM based

### Reflected attack
* you are being attacked
* given a link to follow 
* server is involed
* the link allows the hacker to get the info

* get an email
	the email looks phishy but the link looks trustworthy 
	the hacker found a loop hole and they can run scripts to get data or transfer money ect
	* sanitise the input
	* Escape < and > to &lt and &gt to prevent script tags 

html supports attributes that run JS scripts
	then 
	Escape " and ' to &quot and &x27

* the problem is that there are different ways to escape content 
* in general, use textContent (reads it as text), setAttribute and  similar 

* remove session cookies from JS (HttpOnly) 
* it is possible to limit where the JS comes from
	![[Pasted image 20230327140600.png]]
	* 'unsafe-inline' is bad (allows inline script)
	* 'nonce-SomeThingRandom'
		* need to the nonce to run the script

### stored attacks
* twitter example is a stored attack

### Dom based
* similar to reflected but doesn't need the server


## Insecure Design 
![[Pasted image 20230327141229.png]]


## Security Misconfiguration 
* turn of things you don't need
* change default accounts and password aka. admin admin
* turn off stack traces


* outdated components/software (log4j)


![[Pasted image 20230327142405.png]]