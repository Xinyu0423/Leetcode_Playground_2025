# Solution 1
```Python
class Solution(object):
    def wordBreak(self, s, wordDict):
        """
        :type s: str
        :type wordDict: List[str]
        :rtype: List[str]
        """
        dp = [[] for _ in range(len(s) + 1)]
        dp[0] = [""]
        for i in range(1, len(s) + 1):
            for j in range(i):
                sub_word = s[j :i]
                if sub_word in wordDict and dp[j]:
                    for each_word in dp[j]:
                        if each_word == "":
                            dp[i].append(sub_word)
                        else:
                            dp[i].append(each_word + " " + sub_word)
        return dp[-1]
                        
```