# Solution 1
```Python
class Solution:
    def removeInvalidParentheses(self, s: str) -> List[str]:
        from collections import deque
        queue = deque()
        queue.append(s)
        visited = set()
        visited.add(s)
        res = []
        while queue:
            size = len(queue)
            for i in range(size):
                cur = queue.popleft()
                if self.check_balance(cur):
                    res.append(cur)
                else:
                    for j in range(len(cur)):
                        if cur[j] == '(' or cur[j] == ')':
                            next = cur[:j] + cur[j + 1:]
                            if next not in visited:
                                visited.add(next)
                                queue.append(next)
            if len(res) > 0:
                return res
        return res


    
    def check_balance(self, cur_s):
        balance = 0
        for char in cur_s:
            if char == '(':
                balance += 1
            elif char == ')':
                balance -= 1
                if balance < 0:
                    return False
        return balance == 0
```

# Solution 2
```Python
class Solution:
    def removeInvalidParentheses(self, s: str) -> List[str]:
        self.res = []
        left_rem, right_rem = self.find_num_remove(s)
        self.dfs(s, 0, left_rem, right_rem, 0, "")
        return list(set(self.res))
    

    def find_num_remove(self, s):
        balance = 0
        right_remove = 0
        for char in s:
            if char == '(':
                balance += 1
            elif char == ')':
                if balance > 0:
                    balance -= 1
                else:
                    right_remove += 1
        left_remove = balance
        return left_remove, right_remove
    
    def dfs(self, s, index, left_rem, right_rem, balance, path):
        if index == len(s):
            if left_rem == 0 and right_rem == 0 and balance == 0:
                self.res.append(path)
            return
        if balance < 0:
            return
        if left_rem + right_rem > len(s) - index:
            return
        if s[index] != '(' and s[index] != ')':
            self.dfs(s, index + 1, left_rem, right_rem, balance, path + s[index])
        elif s[index] == '(':
            self.dfs(s, index + 1, left_rem, right_rem, balance + 1, path + s[index])
            if left_rem > 0:
                self.dfs(s, index + 1, left_rem - 1, right_rem, balance, path)
        elif s[index] == ')':
            if balance > 0:
                self.dfs(s, index + 1, left_rem, right_rem, balance - 1, path + s[index])
            if right_rem > 0:
                self.dfs(s, index + 1, left_rem, right_rem - 1, balance, path)
```