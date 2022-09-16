# Remove Covered Intervals

[https://leetcode.com/problems/remove-covered-intervals/](https://leetcode.com/problems/remove-covered-intervals/)

> Given an array `intervals` where `intervals[i] = [li, ri]` represent the interval `[li, ri)`, remove all intervals that are covered by another interval in the list.
>
> The interval `[a, b)` is covered by the interval `[c, d)` if and only if `c <= a` and `b <= d`.
>
> Return _the number of remaining intervals_.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: intervals = [[1,4],[3,6],[2,8]]
> <strong>Output:
> </strong> 2
> <strong>Explanation:
> </strong> Interval [3,6] is covered by [2,8], therefore it is removed.</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: intervals = [[1,4],[2,3]]
> <strong>Output:
> </strong> 1</code></pre>

```
class Solution {
    public int removeCoveredIntervals(int[][] intervals) {
        int res = 0;
        Arrays.sort(intervals, (a, b) -> (a[0] == b[0] ? b[1] - a[1] : a[0] - b[0]));
        int end = Integer.MIN_VALUE;
        for (int[] cur : intervals) {
            if (end < cur[1]) {
                end = cur[1];
                res++;
            }
        }
        return res;
    }
}
```

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>
