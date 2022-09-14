# Meeting Rooms

[https://leetcode.com/problems/meeting-rooms/](https://leetcode.com/problems/meeting-rooms/)

> Given an array of meeting time `intervals` where `intervals[i] = [starti, endi]`, determine if a person could attend all meetings.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: intervals = [[0,30],[5,10],[15,20]]
> <strong>Output:
> </strong> false</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: intervals = [[7,10],[2,4]]
> <strong>Output:
> </strong> true</code></pre>

```
class Solution {
    public boolean canAttendMeetings(int[][] intervals) {
        Arrays.sort(intervals, (a, b) -> (a[0] - b[0]));
        for (int i = 0; i < intervals.length - 1; i++) {
            if (intervals[i][1] > intervals[i + 1][0]) {
                return false;
            }
        }
        return true;
    }
}
```

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>
