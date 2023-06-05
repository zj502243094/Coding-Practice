# Pairs of Songs With Total Durations Divisible by 60

[https://leetcode.com/problems/pairs-of-songs-with-total-durations-divisible-by-60/](https://leetcode.com/problems/pairs-of-songs-with-total-durations-divisible-by-60/)

> You are given a list of songs where the `ith` song has a duration of `time[i]` seconds.
>
> Return _the number of pairs of songs for which their total duration in seconds is divisible by_ `60`. Formally, we want the number of indices `i`, `j` such that `i < j` with `(time[i] + time[j]) % 60 == 0`.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code><strong>Input: time = [30,20,150,100,40]
> </strong><strong>Output: 3
> </strong><strong>Explanation: Three pairs have a total duration divisible by 60:
> </strong>(time[0] = 30, time[2] = 150): total duration 180
> (time[1] = 20, time[3] = 100): total duration 120
> (time[1] = 20, time[4] = 40): total duration 60
> </code></pre>
>
> **Example 2:**
>
> <pre><code><strong>Input: time = [60,60,60]
> </strong><strong>Output: 3
> </strong><strong>Explanation: All three pairs have a total duration of 120, which is divisible by 60.
> </strong></code></pre>

```
class Solution {
    public int numPairsDivisibleBy60(int[] time) {
        int res = 0;
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < time.length; i++) {
            int rem = time[i] % 60;
            int target = 60 - rem;
            if (map.containsKey(target)) {
                res += map.get(target);
            }
            if (rem == 0) {
                map.put(60, map.getOrDefault(60, 0) + 1);
            } else {
                map.put(rem, map.getOrDefault(rem, 0) + 1);
            }
        }
        return res;
    }
}
```
