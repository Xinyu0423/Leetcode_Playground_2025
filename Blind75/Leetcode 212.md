# Solution 1
```Python
class Solution:
    def findWords(self, board: List[List[str]], words: List[str]) -> List[str]:
        m = len(board)
        n = len(board[0])
        res = []
        root = {}
        words = list(set(words))
        for word in words:
            node = root
            for char in word:
                if char not in node:
                    node[char] = {}
                node = node[char]
            node['#'] = word
        for i in range(m):
            for j in range(n):
                if board[i][j] in root:
                    visited = set()
                    visited.add((i, j))
                    self.dfs(i, j, root[board[i][j]], visited, board, m, n, res)
        return list(set(res))




    def dfs(self, i, j, node, visited, board, m, n, res):
        if i < 0 or i >= m or j < 0 or j >= n:
            return
        if '#' in node:
            res.append(node['#'])
        for dx, dy in [[1, 0], [-1, 0], [0, 1], [0, -1]]:
            x = i + dx
            y = j + dy
            if 0 <= x < m and 0 <= y < n:
                if (x, y) not in visited and board[x][y] in node:
                    visited.add((x, y))
                    self.dfs(x, y, node[board[x][y]], visited, board, m, n, res)
                    visited.remove((x, y))
```

# Solution 2(BFS copy会占用大量内存，导致超时)
```Python
class Solution:
    from collections import deque
    def findWords(self, board: List[List[str]], words: List[str]) -> List[str]:
        m = len(board)
        n = len(board[0])
        res = []
        root = {}
        words = list(set(words))
        for word in words:
            node = root
            for char in word:
                if char not in node:
                    node[char] = {}
                node = node[char]
            node['#'] = word
        for i in range(m):
            for j in range(n):
                if board[i][j] in root:
                    self.bfs(i, j, root[board[i][j]], board, m, n, res)
        return res




    def bfs(self, i, j, node, board, m, n, res):
        queue = deque()
        visited = set()
        visited.add((i, j))
        queue.append([i, j, node, visited])
        while queue:
            popped_x, popped_y, popped_node, temp_visited = queue.popleft()
            if '#' in popped_node:
                res.append(popped_node['#'])
                del popped_node['#']
                
            for dx, dy in [[0, 1], [0, -1],[1, 0], [-1, 0]]:
                x = popped_x + dx
                y = popped_y + dy
                # print(visited)
                if 0 <= x < m and 0 <= y < n and (x, y) not in temp_visited:
                    if  board[x][y] in popped_node:
                        copied_visited = copy.copy(temp_visited)
                        copied_visited.add((x, y))
                        queue.append([x, y, popped_node[board[x][y]], copied_visited])
        
```