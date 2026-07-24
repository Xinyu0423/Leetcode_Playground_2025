# Solution 1
```Python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        n = len(height)
        left = 0
        right = n - 1
        max_area = 0
        while left != right:
            width = right - left
            h = min(height[left], height[right])
            max_area = max(max_area, width * h)
            if height[left] < height[right]:
                left += 1
            else:
                right -= 1
        return max_area

        '''
        # how to optimize the code here
        # in order to find the larger area, this way we r traversing all possible rectangles
        # but move larger height bound wont change the area(cause the area is decide from the low height bound)
        # in that case we only need to change the index of left and right which ever one is smaller
        while left != right:
            temp_right = right
            while left != temp_right:
                width = temp_right - left
                h = min(height[left], height[temp_right])
                max_area = max(max_area, width * h)
                temp_right -= 1
            left += 1
        '''

        return max_area
```