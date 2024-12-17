# BIPARTITE GRAPHS
![[Pasted image 20241103151541.png]]
## Lemma 1
![[Pasted image 20241103151610.png]]
## Lemma 2
![[Pasted image 20241103171658.png]]
Lowest common ancestor:
![[Pasted image 20241103173614.png]]
## Lemma 3
![[Pasted image 20241103180129.png]]
# Connectivity

## Strongly Connected
![[Pasted image 20241103181416.png]]
### Lemma
used to prove the strong connectivity test is true. 
![[Pasted image 20241103181444.png]]
### O(m+n) strong connectivity test
![[Pasted image 20241103181537.png]]

# DAG
是否有 directed cycles 决定了是否是 DAG. 
连边方向决定 topological order. 
![[Pasted image 20241103200523.png]]
### Lemma 1
![[Pasted image 20241103202712.png]]
### Lemma 2
![[Pasted image 20241103203716.png]]
### Lemma 3
![[Pasted image 20241103203904.png]]
### Find Topological Order
![[Pasted image 20241103205047.png]]
# Interval Scheduling Problem
![[Pasted image 20241103205936.png]]
Theorem: earliest-finish-time-first algorithm is optimal. 
# Interval Partition
![[Pasted image 20241104101726.png]]
![[Pasted image 20241211204522.png]]
## depth
![[Pasted image 20241211205009.png]]

### Theorem
![[Pasted image 20241104111951.png]]
# Scheduling to Minimizing Lateness
![[Pasted image 20241104112831.png]]
### Algorithm
![[Pasted image 20241104112916.png]]
### Observation 1
![[Pasted image 20241211221002.png]]
### Observation 2
The earliest-deadline-first schedule has no idle time.
### Inversion
![[Pasted image 20241104114247.png]]
### Observation 3
![[Pasted image 20241104114848.png]]
### Observation 4
![[Pasted image 20241104114917.png]]

### Key Claim
Proof method: greedy exchange.
![[Pasted image 20241211220545.png]]
### Optimality
![[Pasted image 20241104121425.png]]
# Shortest Path Problem
## Dijkstra′s algorithm (for single-source shortest paths problem)
![[Pasted image 20241211232329.png]]
![[Pasted image 20241211232350.png]]
### Relaxation Correctness
relaxation 本质上是扩点, 把点放到 S 里面去.
![[Pasted image 20241211233713.png]]
# Minimum Spanning Tree
## cut, cutset
![[Pasted image 20241104195354.png]]
## Spanning Tree
![[Pasted image 20241104195810.png]]
### Cut Property
cut property 可以证明 Kruskal 和 Prim. 具体可以看 greedy_exchange 那个 material. 里面讲得很好. 
### Kruskal’s
![[Pasted image 20241104200015.png]]
### Prim’s
![[Pasted image 20241104200055.png]]
### Reverse-Delete
![[Pasted image 20241104204239.png]]
### Cycle Property
![[Pasted image 20241104203841.png]]
cycle property 保证了 reverse-delete 的正确性.