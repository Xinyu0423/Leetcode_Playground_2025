# Soultion 1
```Python
class Solution(object):
    def kthSmallest(self, mat, k):
        """
        :type mat: List[List[int]]
        :type k: int
        :rtype: int
        """
        import heapq
        sums = mat[0][:]
        for i in range(1, len(mat)):
            new_sum = []
            heap = []
            for j in range(len(sums)):
                heapq.heappush(heap, (sums[j] + mat[i][0], 0))
            
            while heap and len(new_sum) < k:
                total, index = heapq.heappop(heap)
                new_sum.append(total)
                if index + 1 < len(mat[i]):
                    heapq.heappush(heap, (total - mat[i][index] + mat[i][index + 1], index + 1))
            sums = new_sum
        if k <= len(sums):
            return sums[k - 1]
        else:
            return sums[-1]
```