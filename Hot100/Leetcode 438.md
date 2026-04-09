# Solution 1
```Python
class Solution:
    def findAnagrams(self, s: str, p: str) -> List[int]:
        left = 0
        m = len(s)
        n = len(p)
        sorted_p = sorted(p)
        res = []
        for right in range(m):
            if right - left + 1== n:
                if sorted(s[left: right + 1]) == sorted_p:
                    res.append(left)
                    left += 1
                else:
                    left += 1
        return res
```