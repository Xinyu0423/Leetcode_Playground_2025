# Solution 1
```Python
class Solution:
    def pacificAtlantic(self, heights: List[List[int]]) -> List[List[int]]:
        from collections import deque
        n = len(heights)
        m = len(heights[0])
        res = set()
        for i in range(n):
            for j in range(m):
                queue = deque()
                queue.append((i, j))
                visited = set()
                visited.add((i,j))
                pacific = False
                atlantic = False
                while queue:
                    popped_i, popped_j = queue.popleft()
                    for temp_x, temp_y in [[1,0], [-1, 0], [0, 1], [0, -1]]:
                        x = popped_i + temp_x
                        y = popped_j + temp_y
                        if x < 0 or y < 0:
                            pacific = True
                            continue
                        if x >= n or y >= m:
                            atlantic = True
                            continue
                        if 0 <= x < n and 0 <= y< m and heights[popped_i][popped_j] >= heights[x][y] and (x, y) not in visited:
                            queue.append((x, y))
                            visited.add((x,y))
                if pacific and atlantic:
                    res.add((i,j))
        return list(res)
```