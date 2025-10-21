# Solution
```Python
class Solution(object):
    def removeDuplicateLetters(self, s):
        """
        :type s: str
        :rtype: str
        """
        char_map = {}
        for char in s:
            char_map[char] = char_map.get(char, 0) + 1
        stack = []
        visited_map = {}
        for i in range(len(s)):
            if s[i] in visited_map and visited_map[s[i]] == 1:
                char_map[s[i]] -= 1
            else:
                while len(stack) > 0 and stack[-1] > s[i] and char_map[stack[-1]] >= 1:
                    visited_map[stack[-1]] = 0
                    stack.pop()
                stack.append(s[i])
                char_map[s[i]] -= 1
                visited_map[s[i]] = 1
        return ''.join(stack)
```