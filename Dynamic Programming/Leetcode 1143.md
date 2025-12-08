# Solution 1
```Python
class Solution(object):
    def longestCommonSubsequence(self, text1, text2):
        """
        :type text1: str
        :type text2: str
        :rtype: int
        """
        dp = [[0 for _ in range(len(text2))] for _ in range(len(text1))]
        first_row_flag = False
        first_col_flag = False
        for i in range(len(text1)):
            if text1[i] == text2[0] or first_col_flag:
                dp[i][0] = 1
                first_col_flag = True
        
        for j in range(len(text2)):
            if text1[0] == text2[j] or first_row_flag:
                dp[0][j] = 1
                first_row_flag = True

        for i in range(1, len(text1)):
            for j in range(1, len(text2)):
                if text1[i] != text2[j]:
                    dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])
                else:
                    dp[i][j] = dp[i - 1][j - 1] + 1
                    
        return dp[-1][-1]
```

# Solution 2
```Python
class Solution(object):
    def longestCommonSubsequence(self, text1, text2):
        """
        :type text1: str
        :type text2: str
        :rtype: int
        """
        dp = [[0 for _ in range(len(text2)+ 1)] for _ in range(len(text1) + 1)]
        for i in range(1, len(text1) + 1):
            for j in range(1, len(text2) + 1):
                if text1[i - 1] == text2[j - 1]:
                    dp[i][j] = dp[i - 1][j - 1] + 1
                else:
                    dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])
        return dp[-1][-1]
        
```