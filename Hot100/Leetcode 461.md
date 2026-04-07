# Solution 1
```Python
class Solution:
    def hammingDistance(self, x: int, y: int) -> int:
        x_or = x ^ y
        count = 0
        while x_or:
            count += x_or % 2
            x_or //= 2
        return count
```