# Solution 1
```Python
class Trie:

    def __init__(self):
        self.trie_dict = {}
        

    def insert(self, word: str) -> None:
        tree_dict = self.trie_dict
        for char in word:
            if char not in tree_dict:
                tree_dict[char] = {}
            tree_dict = tree_dict[char]
        tree_dict['#'] = '#'

    def search(self, word: str) -> bool:
        tree_dict = self.trie_dict
        for char in word:
            if char not in tree_dict:
                return False
            else:
                tree_dict = tree_dict[char]
        if '#' in tree_dict:
            return True
        return False
        

    def startsWith(self, prefix: str) -> bool:
        tree_dict = self.trie_dict
        for char in prefix:
            if char not in tree_dict:
                return False
            else:
                tree_dict = tree_dict[char]
        return True
        


# Your Trie object will be instantiated and called as such:
# obj = Trie()
# obj.insert(word)
# param_2 = obj.search(word)
# param_3 = obj.startsWith(prefix)
```