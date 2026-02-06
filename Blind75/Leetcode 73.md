# Solution 1
```Python
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        m = len(matrix)
        n = len(matrix[0])
        from collections import deque
        queue = deque()
        visited = set()
        for i in range(m):
            for j in range(n):
                if matrix[i][j] == 0:
                    visited.add((i, j))
        for i in range(m):
            for j in range(n):
                if matrix[i][j] == 0 and (i, j) in visited:
                    for row in range(m):
                        matrix[row][j] = 0
                        # visited.add((row, j))
                    for col in range(n):
                        matrix[i][col] = 0
                        # visited.add((i, col))
        return matrix
```