# Solution 1:
```Python
class Solution(object):
    def findSpecialInteger(self, arr):
        """
        :type arr: List[int]
        :rtype: int
        """
        freq = len(arr) * 0.25
        k = 1
        target_val = arr[0]
        for i in range(1, len(arr)):
            if arr[i] == target_val:
                k += 1
                if k > freq:
                    return target_val
            else:
                target_val = arr[i]
                k = 1
        return arr[0]
        
```