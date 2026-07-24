# Solution 1
```Python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        nums_map = {'2' : ['a', 'b', 'c'],
                    '3' : ['d', 'e', 'f'],
                    '4' : ['g', 'h', 'i'],
                    '5' : ['j', 'k', 'l'],
                    '6' : ['m', 'n', 'o'],
                    '7' : ['p', 'q', 'r', 's'],
                    '8' : ['t', 'u', 'v'],
                    '9' : ['w', 'x', 'y', 'z']
                    }
        if not digits:
            return []
        res = set()
        self.dfs(0, '', digits, res, nums_map)
        return list(res)

    def dfs(self, index, path, digits, res, nums_map):
        if len(path) == len(digits):
            if path not in res:
                res.add(str(path))
            return
        for i in range(len(nums_map[digits[index]])):
            self.dfs(index + 1, path + nums_map[digits[index]][i], digits, res, nums_map)
```