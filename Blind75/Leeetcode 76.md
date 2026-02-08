# Solution 1
```Python
class Solution:
    def minWindow(self, s: str, t: str) -> str:
        counter_t = {}
        window_dict = {}
        left = 0
        valid = 0
        res = ''
        for char in t:
            if char not in counter_t:
                counter_t[char] = 1
            else:
                counter_t[char] += 1
            
        for right in range(len(s)):
            if s[right] not in window_dict:
                window_dict[s[right]] = 1
            else:
                window_dict[s[right]] += 1
            if s[right] in counter_t and window_dict[s[right]] == counter_t[s[right]]:
                valid += 1
            while len(counter_t) == valid:
                if not res or (right - left + 1) < len(res):
                    res = s[left: right + 1]
                window_dict[s[left]] -= 1
                if s[left] in counter_t and window_dict[s[left]] == counter_t[s[left]] - 1:
                    valid -= 1
                if window_dict[s[left]] == 0:
                    del window_dict[s[left]]
                left += 1
        return res
            

```