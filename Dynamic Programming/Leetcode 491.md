# Solution 1
```Python
class Solution(object):
    def findSubsequences(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        dp = [set() for _ in range(len(nums))]
        res = set()
        for i in range(len(nums)):
            dp[i].add((nums[i],))
            for j in range(i):
                if nums[i] >= nums[j]:
                    for seq in dp[j]:
                        dp[i].add(seq + (nums[i],))
            for seq in dp[i]:
                if len(seq) >= 2:
                    res.add(seq)
        return [list(seq) for seq in res]
```
# Solution 2
```Python
class Solution(object):
    def findSubsequences(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        # we define dp[i] represent end with i all possible non-repeating and  non-decreasing subseq
        # state tansfer function
        # if nums[i] >= nums[j]
        # we add sub_seq to dp[i]
        dp =[set() for _ in range(len(nums))]
        temp_res = set()
        res = []
        for i in range(len(nums)):
            dp[i].add(str(nums[i]))
            for j in range(i):
                if nums[i] >= nums[j]:
                    for seq in dp[j]:
                        dp[i].add( seq + ',' + str(nums[i]))
            for seq in dp[i]:
                if seq.count(',') > 0:
                    temp_res.add(seq)
        # print(dp)
        # print(temp_res)
        for temp_list in temp_res:
            splitted_list = temp_list.split(',')
            int_temp_list = []
            for str_nums in splitted_list:
                int_temp_list.append(int(str_nums))
            res.append(int_temp_list)
        return res
```