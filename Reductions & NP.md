![[Pasted image 20241215002419.png]]
![[Pasted image 20241215003533.png]]
## Poly-time reductions
![[Pasted image 20241215003601.png]]
![[Pasted image 20241215003757.png]]
![[Pasted image 20241215125250.png]]
## Independent set
![[Pasted image 20241215004132.png]]
## Vertex Cover
![[Pasted image 20241215103543.png]]
## IS=VC
IS 和 VC 的共性就是他们都在找一个 set of vertices. 
![[Pasted image 20241215103803.png]]
![[Pasted image 20241215104934.png]]
![[Pasted image 20241215112417.png]]
## Set Cover
![[Pasted image 20241215105649.png]]
## Vertex Cover reduces to set cover
![[Pasted image 20241215110541.png]]
lemma: 
![[Pasted image 20241215111200.png]]
![[Pasted image 20241215111459.png]]


## Satisfiability
给定一个 SAT ，我们可以在多项式时间内将其转换为一个 3-SAT. 
![[Pasted image 20241215111828.png]]
## 3-SAT reduces to IS
![[Pasted image 20241215113056.png]]
### Lemma
![[Pasted image 20241215113425.png]]
![[Pasted image 20241215113500.png]]
## Basic reduction strategies
### reduce 基本上是从左往右 reduce
![[Pasted image 20241215113741.png]]
## Decision, Search, and Optimization problems
![[Pasted image 20241215124147.png]]
### Decision Problems vs Search Problems
![[Pasted image 20241215124710.png]]
### Search Problems vs Optimization Problems
![[Pasted image 20241215125052.png]]
## 3-SAT reduces to subset sum
![[Pasted image 20241215130150.png]]
TODO:
## Subset sum reduces to Knapsack
![[Pasted image 20241215202028.png]]

## P
![[Pasted image 20241215152601.png]]
### Some problems in P
![[Pasted image 20241215152709.png]]
## NP
![[Pasted image 20241215153025.png]]
### Certifiers and certificates: satisfiability
![[Pasted image 20241215153715.png]]
### Some problems in NP
![[Pasted image 20241215153853.png]]
## P, NP, and EXP
![[Pasted image 20241215154853.png]]
![[Pasted image 20241215155154.png]]
![[Pasted image 20241215155213.png]]
## NP-complete
![[Pasted image 20241215160447.png]]
### Polynomial transformations
![[Pasted image 20241215160215.png]]
### Prove NP-completeness
![[Pasted image 20241215161220.png]]
![[Pasted image 20241215161028.png]]
### Implications
![[Pasted image 20241215161423.png]]
![[Pasted image 20241215161547.png]]
![[Pasted image 20241215161843.png]]
## 6 Basic NP-Complete Problems
![[Pasted image 20241215163300.png]]
### 3-Dimensional Matching (3DM)
![[Pasted image 20241215164221.png]]
![[Pasted image 20241215164743.png]]
### 3-SAT reduces to 3DM
![[Pasted image 20241215164905.png]]
TODO, 感兴趣自己看 youtube: https://youtu.be/4AkFIcfIMWg?si=BN3yYwdT6h01DC_q
### Travelling Salesman Problem (TSP)
![[Pasted image 20241215183840.png]]
## NP-hard
![[Pasted image 20241215184842.png]]
![[Pasted image 20241215184858.png]]