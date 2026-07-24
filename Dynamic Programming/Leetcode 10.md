# Solution 1
```Python
class Solution(object):
    def isMatch(self, s, p):
        """
        :type s: str
        :type p: str
        :rtype: bool
        """
        dp = [[False for _ in range(len(p) + 1)] for _ in range(len(s) + 1)]
        dp[0][0] = True
        for j in range(1, len(p) + 1):
            if j >= 2 and p[j - 1] == '*':
                dp[0][j] = dp[0][j - 2]
        for i in range(1, len(s) + 1):
            for j in range(1, len(p) + 1):
                if p[j - 1] != '*':
                    if s[i - 1] == p[j - 1] or p[j - 1] == '.':
                        dp[i][j] = dp[i - 1][j - 1]
                else:
                    if j >= 2:
                        dp[i][j] = dp[i][j - 2]
                    if j>= 2 and (s[i - 1] == p[j - 2] or p[j - 2] == '.'):
                        dp[i][j] = dp[i - 1][j] or dp[i][j]
        return dp[-1][-1] 
        
```