# 167. Two Sum II - Input Array Is Sorted
The goal is to find the two numbers which add up to the given target.

As constant extra space should be used, saving the numbers in a extra data structure is not an option. Instead, two pointers can be used to add two numbers. One pointer starts on the left side and one on the right side of the array. Because the array is sorted we can increment the left pointer if the result of the addition is to small or decrement the right pointer if it is to big. If no two numbers add up to the target, an empty list is returned.

## Code
```python
        l, r = 0, len(numbers)-1
        while l < r:
            if numbers[l] + numbers[r] > target:
                r -= 1
                continue
            if numbers[l] + numbers[r] < target:
                l += 1
                continue
            return [l+1, r+1]
        return []
```
