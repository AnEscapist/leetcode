# Description

Given a collection of intervals, merge all overlapping intervals.

**Examples:**
```
Input: [[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]
Explanation: Since intervals [1,3] and [2,6] overlaps, merge them into [1,6].

Input: [[1,4],[4,5]]
Output: [[1,5]]
Explanation: Intervals [1,4] and [4,5] are considered overlapping.
```

# Solution

```python
# Definition for an interval.
# class Interval(object):
#     def __init__(self, s=0, e=0):
#         self.start = s
#         self.end = e

class Solution(object):
    def merge(self, intervals):
        """
        :type intervals: List[Interval]
        :rtype: List[Interval]
        """
        if len(intervals)<=1: return intervals
        intervals.sort(key=lambda x: x.start)
        res = []
        left = intervals[0].start
        right = intervals[0].end
        for i in range(1, len(intervals)):
            if right >= intervals[i].start:
                right = max(right, intervals[i].end)
            else:
                res.append([left, right])
                left = intervals[i].start
                right = intervals[i].end
        res.append([left, right])
        return res
```
