# Binary Serarch Template
```Python
def binary_search(nums, target):
    left = 0
    right = len(nums) -1
    while left < right:
        mid = (left + right) //2
        if nums[mid] < target:
            left = mid + 1
        else:
            right = mid
    if nums[left] == target:
        return left
    else:
        return -1
```