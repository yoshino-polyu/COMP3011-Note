# Weighted Interval Scheduling Problem
分类讨论的时候引入最优子结构. 
![[Pasted image 20241105155458.png]]

## 记忆化
![[Pasted image 20241105102140.png]]

## Optimal value
Dynamic programming algorithms computes optimal value. `M[j]` is value of optimal solution for job `1..j`. Time cost: Main loop is `O(n)`; sorting is `O(nlogn)` 
![[Pasted image 20241105111113.png]]
![[Pasted image 20241105120837.png]]
## Solution
post-processing - "traceback"
![[Pasted image 20241105115558.png]]
# Max Contiguous Subarray
![[Pasted image 20241105155900.png]]
# Monotonically Increasing Subsequence
![[Pasted image 20241105160308.png]]
# Subset Sum Problem
![[Pasted image 20241105163209.png]]
![[Pasted image 20241105163517.png]]

# Knapsack Problem
![[Pasted image 20241105164822.png]]
# Longest Common Subsequence
![[Pasted image 20241105171257.png]]
# Bellman-Ford
edge weights may be negative. 
returns a boolean indicating whether or not there is a negative weight cycle that is reachable from the source. 
if there is a cycle => no solution exists
if there is not => returns the shortest paths and their weight

if G has no negative cycles, the most edges there can be in a shortest path is n-1.
if G has negative cycles, shortest path is with n or more edges.

Pseudo Code Of Bellman-Ford 
BF的状态关键是第一维是 using at most i edges. 
![[Pasted image 20241105181229.png]]
![[Pasted image 20241105181343.png]]
# Travelling Salesman Problem (TSP)
![[Pasted image 20241105200432.png]]
n! -> (n-1)! 是因为一个长为n的环有n种摆放方式, 1/2 是因为 Accounting for Reversals: A tour traversed in the opposite direction is essentially the same tour (due to the cyclical nature). To account for this symmetry, we divide by 2.
