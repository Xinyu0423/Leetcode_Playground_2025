# Solution 1
```Python
class Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        hash_map = {0: 1}
        count = 0
        pre_sum = 0
        for num in nums:
            pre_sum += num
            if pre_sum - k in hash_map:
                count += hash_map[pre_sum - k]
            hash_map[pre_sum] = hash_map.get(pre_sum, 0) + 1
        return count
```