# Solution 1
```Python
class Solution(object):
    def simplifyPath(self, path):
        """
        :type path: str
        :rtype: str
        """
        stack = []
        words = path.split('/')
        for word in words:
            if word == '':
                continue
            elif word == '.':
                continue
            elif word == '..':
                if len(stack) > 0:
                    stack.pop()
            else:
                stack.append(word)
        return '/' + '/'.join(stack)
```