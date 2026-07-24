# Solution 1
```Python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        res = 0
        m = len(grid)
        n = len(grid[0])
        from collections import deque
        queue = deque()
        visited = set()
        for i in range(m):
            for j in range(n):
                if grid[i][j] == '1' and (i, j) not in visited:
                    queue.append([i, j])
                    visited.add((i ,j))
                    res += 1
                    while queue:
                        poped_x, poped_y = queue.popleft()
                        # visited.add((poped_x, poped_y))
                        for dx, dy in [[1,0], [-1, 0], [0, 1], [0, -1]]:
                            x = dx + poped_x
                            y = dy + poped_y
                            if 0 <= x < m and 0 <= y < n and (x, y) not in visited and grid[x][y] == '1':
                                queue.append([x, y])
                                visited.add((x, y))
        return res

```