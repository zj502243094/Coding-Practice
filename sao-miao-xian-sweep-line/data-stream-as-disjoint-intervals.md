# Data Stream as Disjoint Intervals

[https://leetcode.com/problems/data-stream-as-disjoint-intervals/](https://leetcode.com/problems/data-stream-as-disjoint-intervals/)

> Given a data stream input of non-negative integers `a1, a2, ..., an`, summarize the numbers seen so far as a list of disjoint intervals.
>
> Implement the `SummaryRanges` class:
>
> * `SummaryRanges()` Initializes the object with an empty stream.
> * `void addNum(int value)` Adds the integer `value` to the stream.
> * `int[][] getIntervals()` Returns a summary of the integers in the stream currently as a list of disjoint intervals `[starti, endi]`. The answer should be sorted by `starti`.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input
> ["SummaryRanges", "addNum", "getIntervals", "addNum", "getIntervals", "addNum", "getIntervals", "addNum", "getIntervals", "addNum", "getIntervals"]
> [[], [1], [], [3], [], [7], [], [2], [], [6], []]
> <strong>Output
> </strong>[null, null, [[1, 1]], null, [[1, 1], [3, 3]], null, [[1, 1], [3, 3], [7, 7]], null, [[1, 3], [7, 7]], null, [[1, 3], [6, 7]]]
> <strong>Explanation
> </strong>SummaryRanges summaryRanges = new SummaryRanges();
> summaryRanges.addNum(1);      // arr = [1]
> summaryRanges.getIntervals(); // return [[1, 1]]
> summaryRanges.addNum(3);      // arr = [1, 3]
> summaryRanges.getIntervals(); // return [[1, 1], [3, 3]]
> summaryRanges.addNum(7);      // arr = [1, 3, 7]
> summaryRanges.getIntervals(); // return [[1, 1], [3, 3], [7, 7]]
> summaryRanges.addNum(2);      // arr = [1, 2, 3, 7]
> summaryRanges.getIntervals(); // return [[1, 3], [7, 7]]
> summaryRanges.addNum(6);      // arr = [1, 2, 3, 6, 7]
> summaryRanges.getIntervals(); // return [[1, 3], [6, 7]]</code></pre>

```
class SummaryRanges {
    
    TreeSet<int[]> set;
    public SummaryRanges() {
        set = new TreeSet<>((a, b) -> (a[0] == b[0] ? a[1] - b[1] : a[0] - b[0]));
    }
    
    public void addNum(int val) {
        int[] interval = new int[]{val, val};
        if (set.contains(interval)) return;
        int[] low = set.lower(interval);
        int[] high = set.higher(interval);
        if (high != null && high[0] == val) return;
        if (low != null && low[1] + 1 == val && high != null && val + 1 == high[0]) {
            low[1] = high[1];
            set.remove(high);
        } else if (low != null && low[1] + 1 >= val) {
            low[1] = Math.max(low[1], val);
        } else if (high != null && val + 1 == high[0]) {
            high[0] = val;
        } else {
            set.add(interval);
        }
    }
    
    public int[][] getIntervals() {
        List<int[]> res = new ArrayList<>();
        for (int[] interval : set) res.add(interval);
        return res.toArray(new int[0][]);
    }
}
```
