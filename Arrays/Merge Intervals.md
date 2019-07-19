
# Merge Intervals

https://leetcode.com/problems/merge-intervals/

- Time: O(n log n)
- Space: O(n)


```python
class Solution:
    # Time: O(n log n)
    # Space: O(n) for results
    # In the worse case there will be no overlaps
    # And each and every interval would have to be stored
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        
        # corner case
        if len(intervals) <= 1:
            return intervals
        # O(n log n)
        intervals.sort()
        
        results = []
        results.append(intervals[0])
        
        # O(n)
        for i in range(1, len(intervals)):
            # if previous meeting ends on or after current start
            if results[-1][1] >= intervals[i][0]:
                # Extend the top of results stack
                results[-1][1] = max(results[-1][1], intervals[i][1])
            else: # previous has already ended. no overlap
                results.append(intervals[i])
                
        return results
```
