# Solution 1:
```Python
class Solution(object):
    def minimumAbsDifference(self, arr):
        """
        :type arr: List[int]
        :rtype: List[List[int]]
        """
        arr.sort()
        ans = []
        min_subtract= arr[-1] - arr[0]
        for i in range(1, len(arr)):
            if arr[i] - arr[i - 1] < min_subtract:
                ans = [[arr[i - 1], arr[i]]]
                min_subtract = arr[i] - arr[i - 1]
            elif arr[i] - arr[i - 1] == min_subtract:
                ans.append([arr[i - 1], arr[i]])
        return ans

        
```