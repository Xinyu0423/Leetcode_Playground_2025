# Solution 1
```Python
class Solution(object):
    def minOperations(self, logs):
        """
        :type logs: List[str]
        :rtype: int
        """
        stack = []
        for log in logs:
            if log != '../' and log != './':
                stack.append(log)
            elif log == '../' and len(stack) > 0:
                    stack.pop()
            else:
                continue
                
        return len(stack)
```