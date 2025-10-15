# Solution 1
```Python
class Solution(object):
    def buildArray(self, target, n):
        """
        :type target: List[int]
        :type n: int
        :rtype: List[str]
        """
        stack = []
        operations = []
        j = 0
        for i in range(n):
            stack.append(i + 1)
            operations.append("Push")
            if i + 1 != target[j]:
                stack.pop()
                operations.append("Pop")
            else:
                j += 1
            if j == len(target):
                return operations
            
        
```