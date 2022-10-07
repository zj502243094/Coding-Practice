# Employee Free Time

[https://leetcode.com/problems/employee-free-time/](https://leetcode.com/problems/employee-free-time/)

> Return the list of finite intervals representing **common, positive-length free time** for _all_ employees, also in sorted order.
>
> (Even though we are representing `Intervals` in the form `[x, y]`, the objects inside are `Intervals`, not lists or arrays. For example, `schedule[0][0].start = 1`, `schedule[0][0].end = 2`, and `schedule[0][0][0]` is not defined).  Also, we wouldn't include intervals like \[5, 5] in our answer, as they have zero length.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: schedule = [[[1,2],[5,6]],[[1,3]],[[4,10]]]
> <strong>Output:
> </strong> [[3,4]]
> <strong>Explanation:
> </strong> There are a total of three employees, and all common
> free time intervals would be [-inf, 1], [3, 4], [10, inf].
> We discard any intervals that contain inf as they aren't finite.</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: schedule = [[[1,3],[6,7]],[[2,4]],[[2,5],[9,12]]]
> <strong>Output:
> </strong> [[5,6],[7,9]]</code></pre>

```
class Solution {
    public List<Interval> employeeFreeTime(List<List<Interval>> schedule) {
        List<Interval> res = new ArrayList<>();
        PriorityQueue<Interval> pq = new PriorityQueue<>((a, b) -> (a.start - b.start));
        for (List<Interval> list : schedule) {
            for (Interval interval : list) {
                pq.add(interval);
            }
        }
        Interval cur = pq.poll();
        while (!pq.isEmpty()) {
            if (cur.end >= pq.peek().start) {
                cur.end = Math.max(cur.end, pq.poll().end);
            } else {
                res.add(new Interval(cur.end, pq.peek().start));
                cur = pq.poll();
            }
        }
        return res;
    }
}
```

![](<../.gitbook/assets/image (4) (2).png>)
