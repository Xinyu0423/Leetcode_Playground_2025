# Solution 1
```Python
class Solution(object):
    def numDecodings(self, s):
        """
        :type s: str
        :rtype: int
        """
        if s[0] == '0':
            return 0
        dp = [0 for _ in range(len(s) + 1)]
        dp[0] = 1
        if s[0] == '*':
            dp[1] = 9
        else:
            dp[1] = 1
        for i in range(2, len(s) + 1):
            if s[i - 1] != '*':
                if s[i - 1] != '0':
                    dp[i] += dp[i - 1]
                if s[i - 2] == '1':
                    dp[i] += dp[i - 2]
                elif s[i - 2] == '2' and int(s[i - 1]) < 7:
                    dp[i] += dp[i - 2]
                elif s[i - 2] == '*':
                    if int(s[i - 1]) < 7:
                        dp[i] += dp[i - 2] * 2
                    else:
                        dp[i] += dp[i - 2]
            else:
                dp[i] += dp[i - 1] * 9
                if s[i - 2] == '1':
                    dp[i] += dp[i - 2] * 9
                elif s[i - 2] == '2':
                    dp[i] += dp[i - 2] * 6
                elif s[i - 2] == '*':
                    dp[i] += dp[i - 2] * 15
                    
            dp[i] = dp[i] % (10**9 + 7)
        return dp[-1]
```