# Remove Interval

[https://leetcode.com/problems/remove-interval/](https://leetcode.com/problems/remove-interval/)

> You are given a **sorted** list of disjoint intervals `intervals` representing a set of real numbers as described above, where `intervals[i] = [ai, bi]` represents the interval `[ai, bi)`. You are also given another interval `toBeRemoved`.
>
> Return _the set of real numbers with the interval_ `toBeRemoved` _ **removed** from_ `intervals`_. In other words, return the set of real numbers such that every_ `x` _in the set is in_ `intervals` _but **not** in_ `toBeRemoved`_. Your answer should be a **sorted** list of disjoint intervals as described above._
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2020/12/24/removeintervalex1.png)
>
> <pre><code>Input: intervals = [[0,2],[3,4],[5,7]], toBeRemoved = [1,6]
> <strong>Output:
> </strong> [[0,1],[6,7]]</code></pre>
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2020/12/24/removeintervalex2.png)
>
> <pre><code>Input: intervals = [[0,5]], toBeRemoved = [2,3]
> <strong>Output:
> </strong> [[0,2],[3,5]]</code></pre>
>
> **Example 3:**
>
> <pre><code>Input: intervals = [[-5,-4],[-3,-2],[1,2],[3,5],[8,9]], toBeRemoved = [-1,4]
> <strong>Output:
> </strong> [[-5,-4],[-3,-2],[4,5],[8,9]]</code></pre>

```
class Solution {
    public List<List<Integer>> removeInterval(int[][] intervals, int[] toBeRemoved) {
        List<List<Integer>> res = new ArrayList<>();
        for (int[] cur : intervals) {
            if (cur[1] < toBeRemoved[0] || cur[0] > toBeRemoved[1]) {
                res.add(Arrays.asList(cur[0], cur[1]));
            } else {
                if (cur[0] < toBeRemoved[0]) {
                    res.add(Arrays.asList(cur[0], toBeRemoved[0]));
                }
                if (cur[1] > toBeRemoved[1]) {
                    res.add(Arrays.asList(toBeRemoved[1], cur[1]));
                }
            }
        }
        return res;
    }
}
```
