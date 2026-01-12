# Solution 1
```Python
"""
# Definition for a Node.
class Node:
    def __init__(self, val = 0, neighbors = None):
        self.val = val
        self.neighbors = neighbors if neighbors is not None else []
"""

from typing import Optional
class Solution:
    def cloneGraph(self, node: Optional['Node']) -> Optional['Node']:
        self.visited = {}
        return self.dfs(node)

    def dfs(self, node):
        if node is None:
            return None
        if node in self.visited:
            return self.visited[node]
        cloned_node = Node(node.val, [])
        self.visited[node] = cloned_node
        if node.neighbors is not None:
            cloned_neighbors = []
            for each_node in node.neighbors:
                cloned_neighbor = self.dfs(each_node)
                cloned_neighbors.append(cloned_neighbor)
            cloned_node.neighbors = cloned_neighbors
        return cloned_node
```

# Solution 2
```Python
"""
# Definition for a Node.
class Node:
    def __init__(self, val = 0, neighbors = None):
        self.val = val
        self.neighbors = neighbors if neighbors is not None else []
"""

from typing import Optional
class Solution:
    def cloneGraph(self, node: Optional['Node']) -> Optional['Node']:
        from collections import deque
        if not node:
            return None
        queue = deque([node])
        visited = {}
        cloned_node = Node(node.val, [])
        visited[node] = cloned_node
        while queue:
            popped_node = queue.popleft()
            for neighbor in popped_node.neighbors:
                if neighbor not in visited:
                    visited[neighbor] = Node(neighbor.val, [])
                    queue.append(neighbor)
                visited[popped_node].neighbors.append(visited[neighbor])
        return cloned_node

```