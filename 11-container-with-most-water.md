# 11. Container With Most Water
The goal is to find the largest area between two entries in the input array. An area can be drawn between two entries and is calculated as `min(height[l], height[r]) * (r-l)`.

The implementation uses two pointers for comparing entries inside the input array. It starts by calculating the area from the start and end entry. After every comparison the pointer with the smaller value gets shifted.


## Code
```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        res = 0
        l, r = 0, len(height)-1
        while l < r:
            res = max(res, min(height[l], height[r]) * (r-l))
            if height[l] < height[r]:
                l += 1
            else:
                r -= 1
        return res
```
