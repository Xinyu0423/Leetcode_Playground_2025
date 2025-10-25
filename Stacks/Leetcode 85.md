# Solution 1
```Python
class Solution(object):
    def maximalRectangle(self, matrix):
        """
        :type matrix: List[List[str]]
        :rtype: int
        """
        height = [0 for _ in range(len(matrix[0]))]
        max_area = 0
        for i in range(len(matrix)):
            for j in range(len(matrix[0])):
                if matrix[i][j] == '1':
                    height[j] += 1
                else:
                    height[j] = 0
            curr_area = self.largest_rectangle(height)
            max_area = max(max_area, curr_area)
        return max_area
        
    def largest_rectangle(self, height):
        height.append(0)
        stack = []
        res = 0
        for i in range(len(height)):
            while len(stack) > 0 and height[stack[-1]] > height[i]:
                poped_element = stack.pop()
                if len(stack) == 0:
                    width = i
                else:
                    width = i - stack[-1] - 1
                res = max(res, width * height[poped_element])
            stack.append(i)
        return res
```