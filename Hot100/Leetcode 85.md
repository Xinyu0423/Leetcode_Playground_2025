# Solution 1
```Python
class Solution:
    def maximalRectangle(self, matrix: List[List[str]]) -> int:
        m = len(matrix)
        n = len(matrix[0])
        height = [0 for _ in range(n)]
        max_area = 0
        for i in range(m):
            for j in range(n):
                if matrix[i][j] == "1":
                    height[j] += 1
                else:
                    height[j] = 0
            area = self.monotonic_stack(height)
            max_area = max(max_area, area)
        return max_area
    

    def monotonic_stack(self, height):
        height.append(0)
        stack = []
        area = 0
        for i in range(len(height)):
            while stack and height[i] < height[stack[-1]]:
                popped_element = stack.pop()
                if stack:
                    area = max(area, height[popped_element] * (i - stack[-1] - 1))
                else:
                    area = max(area, height[popped_element] * i)
            stack.append(i)
        return area
        
```