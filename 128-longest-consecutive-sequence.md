# 128. Longest Consecutive Sequence
The most obvious solution is to sort the list and loop through it remembering the longest sequence. But this needs O(n * log(n)) time. 

Three attributes of a sequence are that the first value has no predecessor, meaning there exists no element `value-1`. And the last value has no successor (`value+1`). Values inside a sequence do have a predecessor and successor. 

The implementation loops through the list and checks the above mentioned attributes. If the start of a sequence is found the counter is set to 1, and until there is a successor the counter is incremented. The longest sequence is returned in the end.

## Code
```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        s = set(nums)
        longest = 0
        
        for v in nums:
            if v-1 not in s:
                count = 1
                while v+1 in s:
                    count += 1
                    v += 1
                if count > longest:
                    longest = count

        return longest
```
