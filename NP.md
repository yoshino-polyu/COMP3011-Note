是否能在多项式时间复杂度判断一个解是不是他要求的最优解
![[Pasted image 20241105234730.png]]

X 相当于一个问题集
![[Pasted image 20241105234802.png]]

# P=NP?
![[Pasted image 20241105234921.png]]
![[Pasted image 20241105235128.png]]
# NP-complete
An unexpected property of NP problems is that every NP problem reduces to every NP-complete problem. This reduction is also "efficient", in that the problem can be transformed (pre-processed and post-processed) in polynomial time.
This also means that solving any NP-complete problem essentially solves all problems in NP. As of today, there are tens of thousands of known NP-complete problems, but none of them have been solved yet.
说人话就是证明Y是 NP-complete 就要选一个已知的 NP-complete problem X 并证明 Y 是 as hard as X. 
![[Pasted image 20241106001042.png]]
## Certifier
certifier 必须要满足以下两个条件.  
w 见证 s 是 X里面. 
![[Pasted image 20241105230200.png]]
## Subset sum
![[Pasted image 20241106005731.png]]