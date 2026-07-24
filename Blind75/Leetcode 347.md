# Solution 1
```Python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        # using min heap
        nums_dict = {}
        for num in nums:
            if num not in nums_dict:
                nums_dict[num] = 1
            else:
                nums_dict[num] += 1
        min_heap = []
        for key, value in nums_dict.items():
            heapq.heappush(min_heap, (value, key))
            if len(min_heap) > k:
                heapq.heappop(min_heap)
        res = []
        for value, key in min_heap:
            res.append(key)
        return res
```