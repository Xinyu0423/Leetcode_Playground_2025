# Solution 1
```Python
class Solution(object):
    def asteroidCollision(self, asteroids):
        """
        :type asteroids: List[int]
        :rtype: List[int]
        """
        stack = []
        for i in range(len(asteroids)):
            alive_flag = True
            while len(stack) > 0 and stack[-1] > 0 and asteroids[i] < 0:
                if stack[-1] > abs(asteroids[i]):
                    alive_flag= False
                    break
                elif stack[-1] == abs(asteroids[i]):
                    stack.pop()
                    alive_flag= False
                    break
                else:
                    stack.pop()
            if alive_flag == True:
                stack.append(asteroids[i])
        return stack
```