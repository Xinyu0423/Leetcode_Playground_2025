# Solution 1:
```Python
class Solution(object):
    def plusOne(self, digits):
        """
        :type digits: List[int]
        :rtype: List[int]
        """
        if digits[-1] != 9:
            digits[-1] += 1
            return digits
        right = len(digits) - 1
        while digits[right] == 9:
            if right == 0:
                digits[right] = 1
                digits.append(0)
                return digits
            digits[right] = 0
            right -= 1
        digits[right] += 1
        return digits
```