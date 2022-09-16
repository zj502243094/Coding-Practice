# Meeting Scheduler

[https://leetcode.com/problems/meeting-scheduler/](https://leetcode.com/problems/meeting-scheduler/)

> Given the availability time slots arrays `slots1` and `slots2` of two people and a meeting duration `duration`, return the **earliest time slot** that works for both of them and is of duration `duration`.
>
> If there is no common time slot that satisfies the requirements, return an **empty array**.
>
> The format of a time slot is an array of two elements `[start, end]` representing an inclusive time range from `start` to `end`.
>
> It is guaranteed that no two availability slots of the same person intersect with each other. That is, for any two time slots `[start1, end1]` and `[start2, end2]` of the same person, either `start1 > end2` or `start2 > end1`.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: slots1 = [[10,50],[60,120],[140,210]], slots2 = [[0,15],[60,70]], duration = 8
> <strong>Output:
> </strong> [60,68]</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: slots1 = [[10,50],[60,120],[140,210]], slots2 = [[0,15],[60,70]], duration = 12
> <strong>Output:
> </strong> []</code></pre>

```
class Solution {
    public List<Integer> minAvailableDuration(int[][] slots1, int[][] slots2, int duration) {
        List<Integer> res = new ArrayList<>();
        Arrays.sort(slots1, (a, b) -> a[0] - b[0]);
        Arrays.sort(slots2, (a, b) -> a[0] - b[0]);
        int m = slots1.length, n = slots2.length;
        int i = 0, j = 0;
        while (i < m && j < n) {
            int start = Math.max(slots1[i][0], slots2[j][0]);
            int end = Math.min(slots1[i][1], slots2[j][1]);
            if (end - start >= duration) {
                res.add(start);
                res.add(start + duration);
                return res;
            } else if (slots1[i][1] < slots2[j][1]) {
                i++;
            } else {
                j++;
            }
        }
        return res;
    } 
}
```

![](<../.gitbook/assets/image (17).png>)
