# Solution 1
```Python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        n = len(s)
        dp =[[False for _ in range(n)] for _ in range(n)]
        res = ''
        max_length = 0
        for i in range(n - 1, -1, -1):
            for j in range(i, n):
                if s[i] != s[j]:
                    dp[i][j] = False
                else:
                    if i == j:
                        dp[i][j] = True
                    elif j - i == 1:
                        dp[i][j] = True
                    else:
                        dp[i][j] = dp[i + 1][j - 1]
                if dp[i][j] == True and j - i + 1 > max_length:
                    max_length = j - i + 1
                    res = s[i:j + 1]
        return res
```