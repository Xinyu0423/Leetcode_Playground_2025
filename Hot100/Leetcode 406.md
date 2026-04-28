# Solution 1
```Python
class Solution:
    def reconstructQueue(self, people: List[List[int]]) -> List[List[int]]:
        people.sort(key = lambda x :(x[0], -x[1]))
        n = len(people)
        res = [[] for _ in range(n)]
        for person in people:
            space = person[1] + 1
            for i in range(n):
                if not res[i]:
                    space -= 1
                    if space == 0:
                        res[i] = person
                        break
        return res
```