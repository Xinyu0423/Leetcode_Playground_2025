# Solution 1
```Python
class Solution(object):
    def largestRectangleArea(self, heights):
        """
        :type heights: List[int]
        :rtype: int
        """
        heights.append(0)
        stack = []
        res = 0
        for i in range(len(heights)):
            while len(stack) > 0 and heights[stack[-1]] > heights[i]:
                poped_element = stack.pop()
                if len(stack) == 0:
                    wdith = i
                else:
                    wdith = i - stack[-1] - 1
                res = max(res, heights[poped_element] * wdith)
            stack.append(i)
        return res
```