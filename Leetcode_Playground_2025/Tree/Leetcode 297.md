# Solution 1
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def createBinaryTree(self, descriptions):
        """
        :type descriptions: List[List[int]]
        :rtype: Optional[TreeNode]
        """
        node_map = {}
        root = None
        for desc in descriptions:
            node_map[desc[1]] = TreeNode(desc[1])
        for desc in descriptions:
            if desc[0] not in node_map:
                node_map[desc[0]] = TreeNode(desc[0])
                root = node_map[desc[0]]
            if desc[2] == 1:
                node_map[desc[0]].left = node_map[desc[1]]
            else:
                node_map[desc[0]].right = node_map[desc[1]]
        return root
```

# Solution 2
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None


class Codec:

    def serialize(self, root):
        """Encodes a tree to a single string.
        
        :type root: TreeNode
        :rtype: str
        """
        if root is None:
            return ""
        from collections import deque
        queue = deque()
        queue.append(root)
        res = ""
        while queue:
            n = len(queue)
            for _ in range(n):
                poped_element = queue.popleft()
                if poped_element is not None:
                    res += str(poped_element.val) + ','
                    queue.append(poped_element.left)
                    queue.append(poped_element.right)
                else:
                    res += '#,'
        return res

        

    def deserialize(self, data):
        """Decodes your encoded data to tree.
        
        :type data: str
        :rtype: TreeNode
        """
        if not data:
            return None
        self.index = 0
        data = data.split(',')
        if data and data[-1] == '':
            data.pop()
        root = TreeNode(self.get_value(data))
        queue = deque()
        queue.append(root)
        while queue:
            n = len(queue)
            for _ in range(n):
                poped_element = queue.popleft()
                if self.index < len(data) and data[self.index] != '#':
                    poped_element.left = TreeNode(self.get_value(data))
                    queue.append(poped_element.left)
                else:
                    poped_element.left = None
                    self.index += 1
                if self.index < len(data) and data[self.index] != '#':
                    poped_element.right = TreeNode(self.get_value(data))
                    queue.append(poped_element.right)
                else:
                    poped_element.right = None
                    self.index += 1
        return root
                




    def get_value(self, data):
        val = int(data[self.index]) 
        self.index += 1
        return val
        

        

# Your Codec object will be instantiated and called as such:
# ser = Codec()
# deser = Codec()
# ans = deser.deserialize(ser.serialize(root))
```

# Solution 3
```Python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Codec:

    def serialize(self, root):
        """Encodes a tree to a single string.
        
        :type root: TreeNode
        :rtype: str
        """
        print(self.preorder(root))
        return self.preorder(root)

    def preorder(self, root):
        pres = ""
        if root is None:
            return "#"
        else:
            pres += str(root.val) + ','
            pres += self.preorder(root.left)
            pres += self.preorder(root.right)
        return pres
        

    def deserialize(self, data):
        """Decodes your encoded data to tree.
        
        :type data: str
        :rtype: TreeNode
        """
        self.index = 0
        return self.createTree(data)

    def createTree(self, data):
        # if self.index >= len(data):
        #     return None
        if data[self.index] == '#':
            self.index += 1
            return None
        root = TreeNode(self.get_value(data))
        root.left = self.createTree(data)
        root.right = self.createTree(data)
        return root

    def get_value (self, s):
        val = 0
        flag = 1
        while self.index < len(s) and s[self.index] != ',':
            if s[self.index] == '-':
                flag = -1
                self.index += 1
            else:
                val = val * 10 + int(s[self.index])
                self.index += 1
        self.index += 1
        return flag * val
        

# Your Codec object will be instantiated and called as such:
# ser = Codec()
# deser = Codec()
# ans = deser.deserialize(ser.serialize(root))
```