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

# Solution 2
```Python
class Solution(object):
    def kthSmallest(self, mat, k):
        """
        :type mat: List[List[int]]
        :type k: int
        :rtype: int
        """
        left = sum(row[0] for row in mat)
        right = sum(row[-1] for row in mat)
        ans = right

        def count_path(target):
            current_path = [0]
            for i in range(len(mat)):
                new_sums = []
                for j in range(len(mat[i])):
                    for s in current_path:
                        new_sum = s + mat[i][j]
                        if new_sum > target:
                            break
                        new_sums.append(new_sum)
                new_sums.sort()
                if len(new_sums) > k:
                    new_sums = new_sums[: k]
                current_path = new_sums
            return len(current_path)
        
        while left <= right:
            mid = (left + right) // 2
            count = count_path(mid)
            if count >=k:
                ans = mid
                right = mid - 1
            else:
                left = mid + 1
        return ans
```