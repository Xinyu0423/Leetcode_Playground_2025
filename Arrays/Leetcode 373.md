# Soultion 1:
```Python
class Solution(object):
    def kSmallestPairs(self, nums1, nums2, k):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :type k: int
        :rtype: List[List[int]]
        """
        m, n = len(nums1), len(nums2)
        ans = []
        x = [None for _ in range(m)]
        for i in range(m):
            x[i] = [i, 0, nums1[i] + nums2[0]]
        while k > 0:
            mini = self.mink(nums1, nums2, x)
            if mini == -1:
                break
            i, j = nums1[x[mini][0]], nums2[x[mini][1]]
            ans.append([i, j])
            if x[mini][1] + 1 <n:
                i, j = x[mini][0], x[mini][1] + 1
                x[mini] = [i, j, nums1[i] + nums2[j]]
            else:
                x[mini] = [-1, -1, float('inf')]
            k -= 1
        return ans

    def mink(self, a, b, x):
        mini = 0
        for k in range(1, len(x)):
            if x[k][2] < x[mini][2]:
                mini = k
        if x[mini][2] == float('inf'):
            return -1
        else:
            return mini
        
```
Note: Will run over time(won't pass all test cases)