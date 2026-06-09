# Solution 1
```Python
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        self.res = []
        self.dfs(0, [], set(), nums)
        return self.res

    def dfs(self, first, output, visited, nums):
        if first == len(nums):
            self.res.append(list(output))
            return
        for i in range(len(nums)):
            if nums[i] not in visited:
                visited.add(nums[i])
                output.append(nums[i])
                self.dfs(first + 1, output, visited, nums)
                output.remove(nums[i])
                visited.remove(nums[i])
```