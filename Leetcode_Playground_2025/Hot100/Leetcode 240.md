# Solution 1
```Python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        m = len(matrix)
        n = len(matrix[0])
        i = m - 1
        j = 0
        while i >= 0 and j < n:
                if matrix[i][j] == target:
                    return True
                elif matrix[i][j] > target:
                    i -= 1
                elif matrix[i][j] < target:
                    j += 1
        return False
```

# Solution 2
```Python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        for nums in matrix:
            target_index = self.binary_search(nums, target)
            if target_index != -1:
                return True
        return False
        
    
    def binary_search(self, nums, target):
        left = 0
        right = len(nums) - 1
        while left < right:
            middle = (left + right) // 2
            if nums[middle] < target:
                left  = middle +  1
            else:
                right = middle
        if nums[left] == target:
            return left
        else:
            return -1
```