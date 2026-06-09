# Solution 1
```Python
class Solution:
    def trap(self, height: List[int]) -> int:
        stack = []
        water = 0
        for i in range(len(height)):
            while stack and height[stack[-1]] < height[i]:
                popped_elment = stack.pop()
                if len(stack) > 0:
                    curr_height = min(height[stack[-1]], height[i]) - height[popped_elment]
                    width = i - stack[-1] - 1
                    water += curr_height * width
            stack.append(i)
        return water
```