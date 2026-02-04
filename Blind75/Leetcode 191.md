# Solution 1
```Python
class Solution:
    def hammingWeight(self, n: int) -> int:
        bin_str_n = bin(n)
        count = 0
        for i in range(2, len(bin_str_n)):
            if bin_str_n[i] == '1':
                count += 1
        return count
```

# Solution 2
```Python
class Solution:
    def hammingWeight(self, n: int) -> int:
        count = 0
        for i in range(32):
            bit = n & 1
            if bit == 1:
                count += 1
            n = n >> 1
        return count
        
```