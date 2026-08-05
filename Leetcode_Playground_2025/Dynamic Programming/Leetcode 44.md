# Solution 1
```Python
class Solution(object):
    def isMatch(self, s, p):
        """
        :type s: str
        :type p: str
        :rtype: bool
        """
        dp = [[False for _ in range(len(s) + 1)] for _ in range(len(p) + 1)]
        dp[0][0] = True
        for i in range(1, len(p) + 1):
            if p[i - 1] == '*':
                dp[i][0] = dp[i -1][0]
            else:
                dp[i][0] = False

        for i in range(1, len(p) + 1):
            for j in range(1, len(s) + 1):
                if p[i - 1] != '?' and p[i - 1] != '*':
                    dp[i][j] = (s[j - 1] == p[i - 1]) and dp[i -1][j -1]
                elif p [i - 1] == '?':
                    dp[i][j] = dp[i -1][j -1]
                elif  p [i - 1] == '*':
                    dp[i][j] = dp[i -1][j] or dp[i][j -1]
        return dp[-1][-1] 
```