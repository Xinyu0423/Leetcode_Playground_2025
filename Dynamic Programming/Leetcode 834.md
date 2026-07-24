# Solution 1
```Python
class Solution:
    def sumOfDistancesInTree(self, n: int, edges: List[List[int]]) -> List[int]:
        self.n = n
        self.graph =[[] for _ in range(n)]
        for u, v in edges:
            self.graph[u].append(v)
            self.graph[v].append(u)
        self.subtree_size = [1 for _ in range(n)]
        self.dim_sum = [0 for _ in range(n)]
        self.ans = [0 for _ in range(n)]
        self.dfs1(0, -1)
        self.ans[0] = self.dim_sum[0]
        self.dfs2(0, -1)
        return self.ans
    
    def dfs1(self, u, parent):
        for v in self.graph[u]:
            if v == parent:
                continue
            self.dfs1(v, u)
            self.subtree_size[u] += self.subtree_size[v]
            self.dim_sum[u] += self.dim_sum[v] + self.subtree_size[v]
            
    def dfs2(self, u, parent):
        for v in self.graph[u]:
            if v == parent:
                continue
            self.ans[v] = self.ans[u] + self.n - 2*self.subtree_size[v]
            self.dfs2(v, u)
    
```