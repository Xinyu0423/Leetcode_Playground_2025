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