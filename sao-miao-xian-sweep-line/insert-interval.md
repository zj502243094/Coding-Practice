# Insert Interval

[https://leetcode.com/problems/insert-interval/](https://leetcode.com/problems/insert-interval/)

> You are given an array of non-overlapping intervals `intervals` where `intervals[i] = [starti, endi]` represent the start and the end of the `ith` interval and `intervals` is sorted in ascending order by `starti`. You are also given an interval `newInterval = [start, end]` that represents the start and end of another interval.
>
> Insert `newInterval` into `intervals` such that `intervals` is still sorted in ascending order by `starti` and `intervals` still does not have any overlapping intervals (merge overlapping intervals if necessary).
>
> Return `intervals` _after the insertion_.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: intervals = [[1,3],[6,9]], newInterval = [2,5]
> <strong>Output:
> </strong> [[1,5],[6,9]]</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: intervals = [[1,2],[3,5],[6,7],[8,10],[12,16]], newInterval = [4,8]
> <strong>Output:
> </strong> [[1,2],[3,10],[12,16]]
> <strong>Explanation:
> </strong> Because the new interval [4,8] overlaps with [3,5],[6,7],[8,10].</code></pre>

```
class Solution {
    public int[][] insert(int[][] intervals, int[] newInterval) {
        List<int[]> res = new ArrayList<>();
        for (int[] cur : intervals) {
            if (newInterval == null || cur[1] < newInterval[0]) {
                res.add(cur);
            } else if (cur[0] > newInterval[1]) {
                res.addAll(List.of(newInterval, cur));
                newInterval = null;
            } else {
                newInterval[0] = Math.min(cur[0], newInterval[0]);
                newInterval[1] = Math.max(cur[1], newInterval[1]);
            }
        }
        if (newInterval != null) res.add(newInterval);
        return res.toArray(new int[0][]);
    }
}
```
