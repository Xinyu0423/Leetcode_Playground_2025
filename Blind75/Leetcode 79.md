# Solution 1
```Python
class Solution:
    def exist(self, board: List[List[str]], word: str) -> bool:
        from collections import deque   
        m = len(board)
        n = len(board[0])

        if len(word) > m * n:
            return False
        for i in range(m):
            for j in range(n):
                if board[i][j] == word[0]:
                    visited = set()
                    visited.add((i, j))
                    queue = deque()
                    queue.append((i, j, 0, visited))
                    while queue:
                        # print(queue)
                        popped_x, popped_y, matched_index, visited = queue.popleft()
                        if matched_index == len(word) - 1:
                            return True
                        for dx, dy in [(0,1), (0,-1), (1,0), (-1,0)]:
                            x = popped_x + dx
                            y = popped_y + dy
                            if 0 <= x < m and 0 <= y < n:
                                if (x, y) not in visited and board[x][y] == word[matched_index + 1]:
                                    copied_visited = copy.copy(visited)
                                    copied_visited.add((x,y))
                                    queue.append((x, y, matched_index + 1, copied_visited))
        return False
```