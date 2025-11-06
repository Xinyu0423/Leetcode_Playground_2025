# Solution 1
```Python
class Solution(object):
    def numSubmat(self, mat):
        """
        :type mat: List[List[int]]
        :rtype: int
        """
        height = [0 for _ in range(len(mat[0]))]
        res = 0
        for i in range(len(mat)):
            for j in range(len(mat[0])):
                if mat[i][j] == 1:
                    height[j] += 1
                else:
                    height[j] = 0
        
            stack = []
            left = [-1 for _ in range(len(mat[0]))]
            right = [len(mat[0]) for _ in range(len(mat[0]))]
            for i in range(len(mat[0])):
                while len(stack) > 0 and height[stack[-1]] >= height[i]:
                    stack.pop()
                if len(stack) > 0:
                    left[i] = stack[-1]
                else:
                    left[i] = -1
                stack.append(i)
        
            stack = []
            for i in range(len(mat[0]) - 1, -1, -1):
                while len(stack) > 0 and height[stack[-1]] > height[i]:
                    stack.pop()
                if len(stack) > 0:
                    right[i] = stack[-1]
                else:
                    right[i] = len(mat[0])
                stack.append(i)
            # print(left)
            # print(right)
            
            for i in range(len(mat[0])):
                # print( height[i], (i - left[i]),(right[i] - i))
                res += height[i] * (i - left[i]) * (right[i] - i)
        return res
```

# Solution 2
```python
class Solution:
    def countOneDArraySubmatrices(self, vec):
        count = 0
        total = 0
        for val in vec:
            if val == 0:
                count = 0
            else:
                count += 1
            total += count 
        return total

    
    def numSubmat(self, mat: List[List[int]]) -> int:
        m, n = len(mat), len(mat[0])
        result = 0
        for start_row in range(m):
            vec = [1] * n
            for end_row in range(start_row, m):
                for col in range(n):
                    vec[col] = vec[col] & mat[end_row][col]
                result += self.countOneDArraySubmatrices(vec)
        return result
```

# Solution 3
```python
class Solution:
    def numSubmat(self, mat: List[List[int]]) -> int:
        m, n = len(mat), len(mat[0])
        result = 0
        h = [0] * n

        for i in range(m):
            for j in range(n):
                if mat[i][j] == 0:
                    h[j] = 0
                else:
                    h[j] += 1

            stack = []
            count = [0] * n
            for j in range(n):
                # monotonic stack
                while stack and h[stack[-1]] > h[j]:
                    stack.pop()
                if stack:
                    w = j - stack[-1]
                    count[j] = h[j] * w + count[stack[-1]]
                else:
                    w = j + 1
                    count[j] = h[j] * w
                stack.append(j)
                # accumulate count to result
                result += count[j]
        return result
```