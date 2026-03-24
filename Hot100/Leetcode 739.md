# Solution 1
```Python
class Solution:
    def dailyTemperatures(self, temperatures: List[int]) -> List[int]:
        n = len(temperatures)
        stack = []
        res = [0 for _ in range(n)]
        for i in range(n):
            while stack and temperatures[i] > temperatures[stack[-1]]:
                popped_element = stack.pop(-1)
                res[popped_element] = i - popped_element
            stack.append(i)
        return res
```