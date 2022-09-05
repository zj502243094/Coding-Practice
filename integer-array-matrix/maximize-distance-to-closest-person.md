# Maximize Distance to Closest Person

[https://leetcode.com/problems/maximize-distance-to-closest-person/](https://leetcode.com/problems/maximize-distance-to-closest-person/)

&#x20;求到最近的人的最大距离

> You are given an array representing a row of `seats` where `seats[i] = 1` represents a person sitting in the `ith` seat, and `seats[i] = 0` represents that the `ith` seat is empty **(0-indexed)**.
>
> There is at least one empty seat, and at least one person sitting.
>
> Alex wants to sit in the seat such that the distance between him and the closest person to him is maximized.&#x20;
>
> Return _that maximum distance to the closest person_.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2020/09/10/distance.jpg)
>
> <pre><code>Input: seats = [1,0,0,0,1,0,1]
> <strong>Output:2</strong></code></pre>
>
>
>
> <pre><code>Input: seats = [1,0,0,0]
> <strong>Output:3</strong></code></pre>

```
class Solution {
    public int maxDistToClosest(int[] seats) {
        int n = seats.length;
        int met = -1;
        int res = 0;
        for (int i = 0; i < seats.length; i++) {
            if (seats[i] == 1) {
                if (met == -1) {
                    res = Math.max(res, i);
                } else {
                    res = Math.max(res, (i - met) / 2);
                }
                met = i;
            }
        }
        if (seats[n - 1] == 0) res = Math.max(res, n - 1 - met);
        return res;
    }
}
```
