# Solution 1
```Python
class Solution:
    def threeSum(self, nums: list[int]) -> list[list[int]]:
        # for two sum question we r given a list of nums and a target
        # we need to find if there is a combination that equal to target
        # to transfer this question to two sum question we can think about it in this way
        # firstly we can sort the nums list because we won't find any duplicate
        # ex: [1, -1, 0, 1] it will be duplicate
        nums.sort()
        res = []
        for i in range(len(nums) - 2):
            if i > 0 and nums[i - 1] == nums[i]:
                continue
            new_nums = nums[i + 1:]
            pairs = self.twoSum(new_nums, -nums[i])
            # print(pairs)
            for a, b in pairs:
                res.append([nums[i], a, b])
        return res

    def twoSum(self, new_nums, target):
        nums_map = {}
        pairs = set()
        for i in range(len(new_nums)):
            rest = target - new_nums[i]
            if rest in nums_map:
                pairs.add((rest, new_nums[i]))
            nums_map[new_nums[i]] = i
        return pairs
```
