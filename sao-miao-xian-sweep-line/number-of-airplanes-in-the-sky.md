# Number of Airplanes in the Sky

[https://www.lintcode.com/problem/391/](https://www.lintcode.com/problem/391/)

> Given an list `interval`, which are taking off and landing time of the flight. How many airplanes are there at most at the same time in the sky?
>
> If landing and taking off of different planes happen at the same time, we consider landing should happen at first.
>
> Example
>
> **Example 1:**
>
> ```
> Input: [(1, 10), (2, 3), (5, 8), (4, 7)]
> Output: 3
> Explanation:
> The first airplane takes off at 1 and lands at 10.
> The second ariplane takes off at 2 and lands at 3.
> The third ariplane takes off at 5 and lands at 8.
> The forth ariplane takes off at 4 and lands at 7.
> During 5 to 6, there are three airplanes in the sky.
> ```
>
> **Example 2:**
>
> ```
> Input: [(1, 2), (2, 3), (3, 4)]
> Output: 1
> Explanation: Landing happen before taking off.
> ```
>
> <img src="../.gitbook/assets/image (1).png" alt="" data-size="original">

```
/**
 * Definition of Interval:
 * public class Interval {
 *     int start, end;
 *     Interval(int start, int end) {
 *         this.start = start;
 *         this.end = end;
 *     }
 * }
 */

public class Solution {
    /**
     * @param airplanes: An interval array
     * @return: Count of airplanes are in the sky.
     */
    public int countOfAirplanes(List<Interval> airplanes) {
        List<int[]> list = new ArrayList<>();
        for (Interval i : airplanes) {
            list.add(new int[]{i.start, 1});
            list.add(new int[]{i.end, -1});
        }
        Collections.sort(list, (a, b) -> a[0] == b[0] ? a[1] - b[1] : a[0] - b[0]);
        int cnt = 0;
        int res = 0;
        for (int[] i : list) {
            cnt += i[1];
            res = Math.max(res, cnt);
        }
        return res;
    }
}
```
