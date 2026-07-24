# Solution 1:
```Python
class Solution(object):
    def nthUglyNumber(self, n):
        """
        :type n: int
        :rtype: int
        """
        res = [0 for _ in range(n)]
        res[0] = 1
        p2 = 0
        p3 = 0
        p5 = 0
        for i in range(1, n):
            a = res[p2] * 2
            b = res[p3] * 3
            c = res[p5] * 5
            min_num = min(a, b, c)
            if min_num == a:
                p2 += 1
            if min_num == b:
                p3 += 1
            if min_num == c:
                p5 += 1
            res[i] = min_num
        return res[-1]
```