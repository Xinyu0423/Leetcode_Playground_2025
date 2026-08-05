# Solution 1
```Python
class Solution(object):
    def intervalIntersection(self, firstList, secondList):
        """
        :type firstList: List[List[int]]
        :type secondList: List[List[int]]
        :rtype: List[List[int]]
        """
        res = []
        i = 0
        j = 0
        for i in range(len(firstList)):
            for j in range(len(secondList)):
                start = max(firstList[i][0], secondList[j][0])
                end = min(firstList[i][1], secondList[j][1])
                if start <= end:
                    res.append([start, end])
        return res
```