# Solution 1
```Python
class Solution:
    def largestRectangleArea(self, heights: List[int]) -> int:
        heights.append(0)
        stack = []
        area = 0
        for i in range(len(heights)):
            while stack and heights[i] < heights[stack[-1]]:
                popped_element = stack.pop()
                if stack:
                    area = max(area, heights[popped_element] * (i - stack[-1] - 1))
                else:
                    area = max(area, heights[popped_element] * i)
            stack.append(i)
        return area
```