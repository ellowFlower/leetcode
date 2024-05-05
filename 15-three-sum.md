# 15. 3Sum
The goal is to find all triplets which add up to 0.

The trick is to fix one value inside the input list. This reduces the problem to the 2Sum problem. 

The implementation loops over the input list, and for every value solves the 2Sum problem. Two checks are added, to not return duplicates inside the result.

## Code
```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        res = []
        nums.sort()
        for i,n in enumerate(nums):
            if i > 0 and n == nums[i-1]:
                # don't use same value in same position twice
                continue
            l, r = i+1, len(nums)-1
            # following code is basically 2sum solution
            while l < r:
                threeSum = n + nums[l] + nums[r]
                if threeSum > 0:
                    r -= 1
                elif threeSum < 0:
                    l += 1
                else:
                    res.append([n, nums[l], nums[r]])
                    l += 1
                    while nums[l] == nums[l-1] and l < r:
                        # again don't use same value in same position twice
                        l += 1
        return res
```
