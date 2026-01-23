# Solution 1
```Python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        n = len(candidates)
        dp = [[] for _ in range(target + 1)]
        dp[0] = [[]]
        candidates.sort()
        for num in candidates:
            for i in range(num, target + 1):
                for comb in dp[i - num]:
                    new_comb = comb + [num]
                    dp[i].append(new_comb)
        return dp[-1]
```

# Solution 2
```Python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        candidates.sort()
        self.res = []
        self.dfs(0, target, [], candidates)
        return self.res
    
    def dfs(self, start_index, target, path, candidates):
        if target == 0:
            self.res.append(copy.deepcopy(path))
            return
        for i in range(start_index, len(candidates)):
            if candidates[i] <= target:
                path.append(candidates[i])
                self.dfs(i, target - candidates[i], path, candidates)
                path.pop()
```

# Solution 3
```Python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        candidates.sort()
        stack = []
        stack.append((0, target, []))
        res = []
        while stack:
            index, remaining, path = stack.pop()
            if remaining == 0:
                res.append(path)
                continue
            for i in range(index, len(candidates)):
                if candidates[i] > remaining:
                    break
                new_path = path + [candidates[i]]
                stack.append((i, remaining - candidates[i], new_path))
        return res
```