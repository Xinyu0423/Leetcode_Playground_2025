# Solution 1
```Python
class Solution:
    def countBits(self, n: int) -> List[int]:
        res = []
        for i in range(n + 1):
            res.append(bin(i).count('1'))
        return res
```

# Solution 2
```Python
class Solution:
    def countBits(self, n: int) -> List[int]:
        dp = [0 for _ in range(n + 1)]
        for i in range(n + 1):
            dp[i] = dp[i >> 1] + (1 & i)
        return dp
```