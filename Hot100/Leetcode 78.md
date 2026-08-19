# Solution 1
```Python
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        self.res = []
        self.dfs(nums, [], 0)
        return self.res

    def dfs(self, nums, path, index):
        self.res.append(list(path))
        for i in range(index, len(nums)):
            path.append(nums[i])
            self.dfs(nums, path, i + 1)
            path.pop()

```

# Solution 2
```Python
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        self.res = []
        self.dfs(nums, [], 0)
        return self.res

    def dfs(self, nums, path, index):
        if path not in self.res:
            self.res.append(list(path))
            # return #这里不能return 因为进来的时候path为[]
        for i in range(index, len(nums)):
            path.append(nums[i])
            self.dfs(nums, path, i + 1)
            path.pop()

```