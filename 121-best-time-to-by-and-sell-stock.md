# 121. Best Time to Buy and Sell Stock
Finding the best time to buy and sell can also be seen as finding the maximum difference between two values, where the value with the lower index must be smaller than the value with the higher index.

For the solution a pointer `l` is used to represent the buy value and a pointer `r` is used to represent the sell value. After the first two values are compared, the pointers are moved through the array until all relevant values are compared. If a new maximum difference is found the result is updated.

## Code
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        l, r, res = 0, 1, 0

        while r < len(prices):
            res = max(res, prices[r]-prices[l])
            if prices[l] > prices[r]:
                # all values in between l and r are compared already at this point
                l = r
            r += 1

        return res
```
