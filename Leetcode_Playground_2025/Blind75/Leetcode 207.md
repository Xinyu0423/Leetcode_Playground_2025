# Solution 1
```Python
class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        from collections import deque
        adj_list = [[] for _ in range(numCourses)]
        indegree = [0 for _ in range(numCourses)]
        for course, pre in prerequisites:
            adj_list[pre].append(course)
            indegree[course] += 1
        print(adj_list, indegree)
        queue = deque()
        for i in range(numCourses):
            if indegree[i] == 0:
                queue.append(i)
        while queue:
            popped_node = queue.popleft()
            for i in adj_list[popped_node]:
                indegree[i] -= 1
                if indegree[i] == 0:
                    queue.append(i)
        for i in range(numCourses):
            if indegree[i] != 0:
                return False
        return True
```