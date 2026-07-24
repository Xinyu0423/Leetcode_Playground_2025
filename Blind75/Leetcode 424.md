# Solution 1
```Python
class Solution:
    def characterReplacement(self, s: str, k: int) -> int:
        left = 0
        right = 0
        count = [0 for _ in range(26)]
        max_count = 0
        max_length = 1
        for right in range(len(s)):
            index = ord(s[right]) - ord('A')
            count[index] += 1
            max_count = max(max_count, count[index])
            while right - left + 1 - max_count > k:
                index = ord(s[left]) - ord('A')
                count[index] -= 1
                left += 1
            max_length = max(max_length, right - left + 1)
        return max_length
```