# Solution 1
```Python
class Solution(object):
    def trap(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        height.append(0)
        stack = []
        res = 0
        for i in range(len(height)):
            while len(stack) > 0 and height[stack[-1]] < height[i]:
                poped_element = stack.pop()
                if len(stack) > 0:
                    h = min(height[i], height[stack[-1]]) - height[poped_element]
                    width = i - stack[-1] - 1
                    res += h  * width
            
            stack.append(i)
        return res
```