# Solution 1
```Python
class WordDictionary:

    def __init__(self):
        self.root = {}

        

    def addWord(self, word: str) -> None:
        node = self.root
        for char in word:
            if char not in node:
                node[char] = {}
            node = node[char]
        node['#'] = '#'

    def search(self, word: str) -> bool:
        from collections import deque
        queue = deque()
        queue.append((self.root, 0))
        while queue:
            node, index = queue.popleft()
            if index == len(word):
                if '#' in node:
                    return True
                continue
            char = word[index]
            if char == '.':
                for key in node:
                    if key != '#':
                        queue.append((node[key], index + 1))
            else:
                if char in node:
                    queue.append((node[char], index + 1))
        return False



# Your WordDictionary object will be instantiated and called as such:
# obj = WordDictionary()
# obj.addWord(word)
# param_2 = obj.search(word)
```