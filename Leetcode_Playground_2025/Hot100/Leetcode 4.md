# Solution 1
```Python
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        if len(nums1) > len(nums2):
            nums1, nums2 = nums2, nums1
        m = len(nums1)
        n = len(nums2)
        half = (m + n + 1) // 2
        left = 0
        right = m
        while left < right:
            i = (left + right + 1) // 2
            j = half - i
            if nums1[i - 1] > nums2[j]:
                right = i - 1
            else:
                left = i
        i = left
        j = half - i
        if i > 0:
            L1 = nums1[i - 1]
        else:
            L1 = float('-inf')
        if i < m:
            R1 = nums1[i]
        else:
            R1 = float('inf')
        if j > 0:
            L2 = nums2[j - 1]
        else:
            L2 = float('-inf')
        if j < n:
            R2 = nums2[j]
        else:
            R2 = float('inf')
        if (m + n) % 2 == 1:
            return max(L1, L2)
        else:
            return (max(L1, L2) + min(R1, R2))/2.0
```

# Solution 2
```Python
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        m = len(nums1)
        n = len(nums2)
        if (m + n) % 2 == 1:
            return self.find_kth(nums1, nums2, ((m + n) + 1) // 2)
        else:
            return (self.find_kth(nums1, nums2, (m + n) // 2)+self.find_kth(nums1, nums2, (m + n)// 2 + 1))/2 

    def find_kth(self, nums1, nums2, k):
        i = 0
        j = 0
        while True:
            if i == len(nums1):
                return nums2[j + k - 1]
            if j == len(nums2):
                return nums1[i + k - 1]
            if k == 1:
                return min(nums1[i], nums2[j])
            step = k // 2
            p1 = min(i + step, len(nums1))
            p2 = min(j + step, len(nums2))
            if nums1[p1 - 1] < nums2[p2 - 1]:
                k -= p1 - i
                i = p1
            else:
                k -= p2 -j
                j = p2
    
```