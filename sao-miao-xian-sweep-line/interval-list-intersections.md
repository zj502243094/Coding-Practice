# Interval List Intersections

[https://leetcode.com/problems/interval-list-intersections/](https://leetcode.com/problems/interval-list-intersections/)

> A **closed interval** `[a, b]` (with `a <= b`) denotes the set of real numbers `x` with `a <= x <= b`.
>
> The **intersection** of two closed intervals is a set of real numbers that are either empty or represented as a closed interval. For example, the intersection of `[1, 3]` and `[2, 4]` is `[2, 3]`.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2019/01/30/interval1.png)
>
> <pre><code>Input: firstList = [[0,2],[5,10],[13,23],[24,25]], secondList = [[1,5],[8,12],[15,24],[25,26]]
> <strong>Output:
> </strong> [[1,2],[5,5],[8,10],[15,23],[24,24],[25,25]]</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: firstList = [[1,3],[5,9]], secondList = []
> <strong>Output:
> </strong> []</code></pre>

```
class Solution {
    public int[][] intervalIntersection(int[][] firstList, int[][] secondList) {
        List<int[]> res = new ArrayList<>();
        Arrays.sort(firstList, (a, b) -> a[0] - b[0]);
        Arrays.sort(secondList, (a, b) -> a[0] - b[0]);
        int m = firstList.length, n = secondList.length;
        int i = 0, j = 0;
        while (i < m && j < n) {
            int start = Math.max(firstList[i][0], secondList[j][0]);
            int end = Math.min(firstList[i][1], secondList[j][1]);
            if (start <= end) res.add(new int[]{start, end});
            if (firstList[i][1] < secondList[j][1]) {
                i++;
            } else {
                j++;
            }
        }
        return res.toArray(new int[0][]);
    }
}
```
