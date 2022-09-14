# Meeting Rooms II

[https://leetcode.com/problems/meeting-rooms-ii/](https://leetcode.com/problems/meeting-rooms-ii/)

> Given an array of meeting time intervals `intervals` where `intervals[i] = [starti, endi]`, return _the minimum number of conference rooms required_.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: intervals = [[0,30],[5,10],[15,20]]
> <strong>Output:
> </strong> 2</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: intervals = [[7,10],[2,4]]
> <strong>Output:
> </strong> 1</code></pre>

```
class Solution {
    public int minMeetingRooms(int[][] intervals) {
        List<int[]> list = new ArrayList<>();
        for (int[] i : intervals) {
            list.add(new int[]{i[0], 1});
            list.add(new int[]{i[1], -1});
        }
        Collections.sort(list, (a, b) -> a[0] == b[0] ? a[1] - b[1] : a[0] - b[0]);
        int res = 0, cnt = 0;
        for (int[] i : list) {
            cnt += i[1];
            res = Math.max(res, cnt);
        }
        return res;
    }
}
```

```
class Solution {
    public int minMeetingRooms(int[][] intervals) {
        Arrays.sort(intervals, (a, b) -> (a[0] - b[0]));
        PriorityQueue<int[]> pq = new PriorityQueue<>((a, b) -> (a[1] - b[1]));
        pq.add(intervals[0]);
        for (int i = 1; i < intervals.length; i++) {
            int[] cur = pq.poll();
            if (cur[1] <= intervals[i][0]) cur[1] = intervals[i][1];
            else pq.add(intervals[i]);
            pq.add(cur);
        }
        return pq.size();
    }
}
```
