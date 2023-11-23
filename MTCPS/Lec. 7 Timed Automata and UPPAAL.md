Uppaal is a model checker

## Train crossing example
![[Pasted image 20230608184243.png]]![[Pasted image 20230608184252.png]]![[Pasted image 20230608184305.png]]
![[Pasted image 20230608184329.png]]

expressions P and Q must be type safe, side effect free and evaluate to a boolean
* validation properties
	* possibly: E<>P                                                   ![[Pasted image 20230608184956.png]]
* Safety Properties
	* Invariant A[]P
	* Pos.Inv.: E[]P                                      ![[Pasted image 20230608185110.png]]
* Liveness Properties
	* Eventually: A<>P
	* Leadsto: P -> Q                              ![[Pasted image 20230608185251.png]]
* Bounded liveness
	* Leads to within: P ->$_{\leq t}$ Q                            ![[Pasted image 20230608185355.png]]


## Verification Engine & Options
![[Pasted image 20230608185654.png]]


![[Pasted image 20230611182649.png]]