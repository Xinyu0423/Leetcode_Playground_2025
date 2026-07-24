# Solution 1
```Python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        if not s:
            return 0
        res = 1
        for i in range(len(s)):
            for j in range(i, len(s) + 1):
                if  len(s[i:j]) == len(set(s[i:j])):
                    res = max(res, len(s[i:j]))
                else:
                    break
        return res
```

# Solution 2
```Python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        char_set = set()
        left = 0
        res = 0
        for right in range(len(s)):
            while s[right] in char_set:
                char_set.remove(s[left])
                left += 1
            char_set.add(s[right])
            res = max(res, right - left + 1)
        return res
```

# Solution 3
```Python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        char_map ={}
        left = 0
        res = 0
        for right in range(len(s)):
            current_char = s[right]
            if s[right] in char_map and char_map[current_char] >= left:
                left = char_map[current_char] + 1
            char_map[current_char] = right
            res = max(res, right - left + 1)
        return re
```