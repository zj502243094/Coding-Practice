# Merge Intervals

[https://leetcode.com/problems/merge-intervals/](https://leetcode.com/problems/merge-intervals/)

> Given an array of `intervals` where `intervals[i] = [starti, endi]`, merge all overlapping intervals, and return _an array of the non-overlapping intervals that cover all the intervals in the input_.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: intervals = [[1,3],[2,6],[8,10],[15,18]]
> Output: [[1,6],[8,10],[15,18]]
> Explanation: Since intervals [1,3] and [2,6] overlap, merge them into [1,6].
> ```
>
> **Example 2:**
>
> ```
> Input: intervals = [[1,4],[4,5]]
> Output: [[1,5]]
> Explanation: Intervals [1,4] and [4,5] are considered overlapping.
> ```

{% hint style="info" %}
对intervals里面的每个元素的第一个数 进行排序 先加入第一个interval后每次进行比较合并
{% endhint %}

```
class Solution {
    public int[][] merge(int[][] intervals) {
        Arrays.sort(intervals, (a, b) -> a[0] - b[0]);
        List<int[]> res = new ArrayList<>();
        int[] cur = intervals[0];
        res.add(cur);
        for (int[] inter : intervals) {
            if (inter[0] <= cur[1]) {
                cur[1] = Math.max(inter[1], cur[1]);
            } else {
                cur = inter;
                res.add(cur);
            }
        }
        return res.toArray(new int[0][]);
    }
}
```

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>
