# Solution 1
```Python
class Solution:
    def insert(self, intervals: list[list[int]], newInterval: list[int]) -> list[list[int]]:
        copied_interval = copy.deepcopy(intervals)
        copied_interval.append(newInterval)
        copied_interval.sort()
        res = [copied_interval[0]]
        for i in range(1, len(copied_interval)):
            if res[-1][1] >= copied_interval[i][0]:
                res[-1] = ([res[- 1][0], max(res[-1][1], copied_interval[i][1])])
            else:
                res.append(copied_interval[i])
        return res
```
