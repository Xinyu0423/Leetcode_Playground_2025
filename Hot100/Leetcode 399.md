# Solution 1
```Python
class Solution:
    def calcEquation(self, equations: List[List[str]], values: List[float], queries: List[List[str]]) -> List[float]:
        self.graph = {}
        for (u, v), val in zip(equations, values):
            if u not in self.graph:
                self.graph[u] = [(v, val)]
            else:
                self.graph[u].append((v, val))
                
            if v not in self.graph:
                self.graph[v] = [(u, 1.0/val)]
            else:
                self.graph[v].append((u, 1.0/val))

        res = []
        for x, y in queries:
            if x not in self.graph or y not in self.graph:
                res.append(-1)
            elif x == y:
                res.append(1)
            else:
                temp_res = self.dfs(x, y, set(), 1.0)
                res.append(temp_res)
        return res
        

    
    def dfs(self,current, target, visited, product):
        if current == target:
            return product
        visited.add(current)
        for neighbor, weight in self.graph[current]:
            if neighbor not in visited:
                res = self.dfs(neighbor, target, visited, product * weight)
                if res != - 1.0:
                    return res
        return -1.0

```