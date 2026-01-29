# Solution 1
```Python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        res_dict = {}
        for i in range(len(strs)):
            char_count = self.create_char_dict(strs[i])
            key = tuple(char_count)
            if key in res_dict:
                res_dict[key].append(strs[i])
            else:
                res_dict[key] = [strs[i]]
        
        return list(res_dict.values())

    
    def create_char_dict(self, s):
        char_count = [0 for _ in range(26)]
        for char in s:
            char_count[ord(char) - ord('a')] += 1
        return char_count
            
```