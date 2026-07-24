# Solution 1
```Python
class doubleLinkedList:
    def __init__(self, key, val):
        self.key = key
        self.val = val
        self.pre = None
        self.next = None
class LRUCache:

    def __init__(self, capacity: int):
        self.capacity = capacity
        self.cache = dict()
        self.head = doubleLinkedList(-1, -1)
        self.tail = doubleLinkedList(-1, -1)
        self.tail.pre = self.head
        self.head.next = self.tail
        

    def get(self, key: int) -> int:
        if key not in self.cache:
            return -1
        else:
            node = self.cache[key]
            self.remove(node)
            self.append(node)
            return node.val
    

    def put(self, key: int, value: int) -> None:
        if key in self.cache:
            self.cache[key].val = value
            self.remove(self.cache[key])
            self.append(self.cache[key])
        else:
            new_node = doubleLinkedList(key, value)
            if len(self.cache) >= self.capacity:
                lru = self.head.next
                self.remove(lru)
                del self.cache[lru.key]
            self.cache[key] = new_node
            self.append(new_node)

    
    def remove(self, node):
        node.pre.next = node.next
        node.next.pre = node.pre
    
    def append(self, node):
        self.tail.pre.next = node
        node.next = self.tail
        node.pre = self.tail.pre
        self.tail.pre = node
        




# Your LRUCache object will be instantiated and called as such:
# obj = LRUCache(capacity)
# param_1 = obj.get(key)
# obj.put(key,value)
```