# Description

Given a set of non-overlapping intervals, insert a new interval into the intervals (merge if necessary).
You may assume that the intervals were initially sorted according to their start times.

**Examples:**

```
Input: intervals = [[1,3],[6,9]], newInterval = [2,5]
Output: [[1,5],[6,9]]

Input: intervals = [[1,2],[3,5],[6,7],[8,10],[12,16]], newInterval = [4,8]
Output: [[1,2],[3,10],[12,16]]
Explanation: Because the new interval [4,8] overlaps with [3,5],[6,7],[8,10].
```

# Solution: 

* First append the new interval, then merge all the intervals

```python
# Definition for an interval.
# class Interval(object):
#     def __init__(self, s=0, e=0):
#         self.start = s
#         self.end = e

class Solution(object):
    def insert(self, intervals, newInterval):
        """
        :type intervals: List[Interval]
        :type newInterval: Interval
        :rtype: List[Interval]
        """
        intervals.append(newInterval)
        if len(intervals)<=1: return intervals
        intervals.sort(key=lambda x: x.start)
        left = intervals[0].start
        right = intervals[0].end
        res = []
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
