
# BIPARTITE GRAPHS
![[Pasted image 20241103151541.png]]
## Lemma 1
![[Pasted image 20241103151610.png]]
## Lemma 2
![[Pasted image 20241103171658.png]]
![[Pasted image 20241103173614.png]]

## Lemma 3
![[Pasted image 20241103180129.png]]
# Connectivity

## Strongly Connected
![[Pasted image 20241103181416.png]]
### Lemma
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

### find topological order
![[Pasted image 20241103205047.png]]
# Interval Scheduling Problem
![[Pasted image 20241103205936.png]]
### Lemma 1
理解这个证明的关键是理解发生overlapping的条件. f
![[Pasted image 20241103214420.png]]
![[Pasted image 20241103214446.png]]
### Lemma 2
利用 lemma 1
![[Pasted image 20241103220752.png]]
# Interval Partition
![[Pasted image 20241104101726.png]]
![[Pasted image 20241104105556.png]]
### Theorem
![[Pasted image 20241104111951.png]]
# Scheduling to Minimizing Lateness
![[Pasted image 20241104112831.png]]
### Algorithm
![[Pasted image 20241104112916.png]]
### Inversion
![[Pasted image 20241104114247.png]]

### Observation 3
![[Pasted image 20241104114848.png]]
### Observation 4
![[Pasted image 20241104114917.png]]

### Key Claim
![[Pasted image 20241104121040.png]]

### Optimality
![[Pasted image 20241104121425.png]]
# Shortest Path Problem
![[Pasted image 20241104123216.png]]
### Relaxation Correctness
relaxation本质上是扩点, 把点放到 S 里面去. 
![[Pasted image 20241104174513.png]]

![[Pasted image 20241104221121.png]]

# Minimum Spanning Tree
## cut, cutset
![[Pasted image 20241104195354.png]]
## spanning tree
![[Pasted image 20241104195810.png]]
### Kruskal’s
![[Pasted image 20241104200015.png]]
### Prim’s
![[Pasted image 20241104200055.png]]
### Reverse-Delete
![[Pasted image 20241104204239.png]]

### Cut Property
Assume 不包含 e, 但必存在 e' 保证连通, cost(e') > cost(e), 反证
![[Pasted image 20241104203151.png]]
cut property 保证了 Prim’s 和 Kruskal’s 的正确性

### Cycle Property
![[Pasted image 20241104203841.png]]
cycle property 保证了 reverse-delete 的正确性
