# Solution 1
```Python
class Solution:
    def spiralOrder(self, matrix: List[List[int]]) -> List[int]:
        m = len(matrix)
        n = len(matrix[0])
        res = []
        left = 0
        right = n -1
        top = 0
        bottom = m - 1
        count = 0
        while count < m * n:
            for i in range(left, right + 1):
                res.append(matrix[left][i])
                count += 1
            
            for j in range(top + 1, bottom + 1):
                res.append(matrix[j][right])
                count += 1
            
            if left < right and top < bottom:
                for j in range(right - 1, left, -1):
                    res.append(matrix[bottom][j])
                    count += 1
                
                for i in range(bottom, top, -1):
                    res.append(matrix[i][left])
                    count += 1
            left += 1
            right -= 1
            top += 1
            bottom -= 1
        return res
```