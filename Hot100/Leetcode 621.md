# Solution 1
```Python
class Solution:
    def leastInterval(self, tasks: List[str], n: int) -> int:
        max_freq = 0
        counter = {}
        for char in tasks:
            if char not in counter:
                counter[char] = 1
            else:
                counter[char] += 1
            max_freq = max(max_freq, counter[char])
        count_max_freq = 0
        for each_task in counter:
            if counter[each_task] == max_freq:
                count_max_freq += 1
        return max((max_freq - 1) *( n + 1) + count_max_freq, len(tasks))
```