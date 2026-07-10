# Solution 1
```Python
class Solution:
    def isMatch(self, s: str, p: str) -> bool:
        # define dp[i][j] repesent pattern's first j char can match s's first i chars
        # initialization: dp[0][0] True
        # for the first row, it means all s r empty, so it always be False
        # for the first col, the patten need to match with empty strings s
        # in that case, we have to have p = x* or p = '.*'
        # state tranfer function
        # if p[j - 1] equal to not equal to * which means it can be any char or '.'
        # then in that case the current char have to be excatly match
        # which means s[i- 1] == p[j - 1] or p[j - 1] == '.'
        # then dp[i][j] = dp[i - 1][j - 1]
        # if p[j - 1] is equal to '*'
        # then there r 2 subcases
        # first we match 0 times(which means we ignore 'x*')
        # then dp[i][j] = dp[i][j - 2]
        # second subcase is it match 1 or more times using x* or .*
        # if s[i - 1] == p[j - 2] or p[j - 2] =='.'
        # then dp[i][j] = dp[i - 1][j] or dp[i][j - 2]
        m = len(s)
        n = len(p)
        dp = [[False for _ in range(n + 1)] for _ in range(m + 1)]
        dp[0][0] = True
        for i in range(1, m + 1):
            dp[i][0] = False
        for j in range(1, n + 1):
            if p[j - 1] == '*' and j > 1:
                dp[0][j] = dp[0][j - 2]
            else:
                dp[0][j] = False

        for i in range(1, m + 1):
            for j in range(1, n +1):
                if p[j - 1] != '*':
                    if s[i - 1] == p[j - 1] or p[j - 1] == '.':
                        dp[i][j] = dp[i - 1][j - 1]
                else:
                    if s[i - 1] != p[j - 2] and p[j - 2] != '.':
                        dp[i][j] = dp[i][j - 2]
                    elif s[i - 1] == p[j - 2] or p[j - 2] == '.':
                        dp[i][j] = dp[i - 1][j] or dp[i][j - 2]
        return dp[-1][-1]
```