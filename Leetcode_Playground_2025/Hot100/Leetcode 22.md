# Solution 1
```Python
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        self.res =[]
        self.dfs("", 0, 0, n)
        return self.res
        
    def dfs(self, curr, left_count, right_count, n):
        if left_count == n and right_count == n:
            self.res.append(curr)
            return
        if left_count < n:
            self.dfs(curr + '(', left_count + 1, right_count, n)
        if left_count > right_count:
            self.dfs(curr + ')', left_count, right_count + 1, n)
        return
```