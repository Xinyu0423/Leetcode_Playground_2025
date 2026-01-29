# Solution 1
```Python
class Solution:
    def eraseOverlapIntervals(self, intervals: List[List[int]]) -> int:
        intervals.sort(key = lambda x: x[1])
        count = 1
        end = intervals[0][1]
        for i in range(1, len(intervals)):
            if intervals[i][0] >= end:
                count += 1
                end = intervals[i][1]
        return len(intervals) - count
```

# Solution 2(会超时)
```Python
class Solution:
    def eraseOverlapIntervals(self, intervals: List[List[int]]) -> int:
        dp = [1 for _ in range(len(intervals))]
        intervals.sort(key = lambda x: x[0])
        for i in range(1, len(intervals)):
            prev_start = intervals[i][0]
            for j in range(i):
                if intervals[j][1] <= prev_start:
                    dp[i] = max(dp[i - 1], dp[j] + 1)
        return len(intervals) - dp[-1]
```