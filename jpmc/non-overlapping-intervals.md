# Non-overlapping Intervals

[https://leetcode.com/problems/non-overlapping-intervals/](https://leetcode.com/problems/non-overlapping-intervals/)

> Given an array of intervals `intervals` where `intervals[i] = [starti, endi]`, return _the minimum number of intervals you need to remove to make the rest of the intervals non-overlapping_.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: intervals = [[1,2],[2,3],[3,4],[1,3]]
> <strong>Output:
> </strong> 1
> <strong>Explanation:
> </strong> [1,3] can be removed and the rest of the intervals are non-overlapping.
> </code></pre>
>
> **Example 2:**
>
> <pre><code>Input: intervals = [[1,2],[1,2],[1,2]]
> <strong>Output:
> </strong> 2
> <strong>Explanation:
> </strong> You need to remove two [1,2] to make the rest of the intervals non-overlapping.
> </code></pre>
>
> **Example 3:**
>
> <pre><code>Input: intervals = [[1,2],[2,3]]
> <strong>Output:
> </strong> 0
> <strong>Explanation:
> </strong> You don't need to remove any of the intervals since they're already non-overlapping.
> </code></pre>

{% hint style="info" %}
If conflict always remove the current one, to leave more space for the later
{% endhint %}

```
class Solution {
    public int eraseOverlapIntervals(int[][] intervals) {
        int res = 0;
        Arrays.sort(intervals, (a, b) -> a[1] - b[1]);
        int end = Integer.MIN_VALUE;
        for (int[] cur : intervals) {
            if (end <= cur[0]) {
                end = cur[1];
            } else {
                res++;
            }
        }
        return res;
    }
}
```
