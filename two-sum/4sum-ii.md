# 4Sum II

[https://leetcode.com/problems/4sum-ii/](https://leetcode.com/problems/4sum-ii/)

> Given four integer arrays `nums1`, `nums2`, `nums3`, and `nums4` all of length `n`, return the number of tuples `(i, j, k, l)` such that:
>
> * `0 <= i, j, k, l < n`
> * `nums1[i] + nums2[j] + nums3[k] + nums4[l] == 0`
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: nums1 = [1,2], nums2 = [-2,-1], nums3 = [-1,2], nums4 = [0,2]
> <strong>Output:
> </strong> 2
> <strong>Explanation:
> </strong>The two tuples are:
> 1. (0, 0, 0, 1) -> nums1[0] + nums2[0] + nums3[0] + nums4[1] = 1 + (-2) + (-1) + 2 = 0
> 2. (1, 1, 0, 0) -> nums1[1] + nums2[1] + nums3[0] + nums4[0] = 2 + (-1) + (-1) + 0 = 0</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: nums1 = [0], nums2 = [0], nums3 = [0], nums4 = [0]
> <strong>Output:
> </strong> 1</code></pre>

```
class Solution {
    public int fourSumCount(int[] nums1, int[] nums2, int[] nums3, int[] nums4) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums1.length; i++) {
            for (int j = 0; j < nums2.length; j++) {
                int sum = nums1[i] + nums2[j];
                map.put(sum, map.getOrDefault(sum, 0) + 1);
            }
        }
        int res = 0;
        for (int i = 0; i < nums3.length; i++) {
            for (int j = 0; j < nums4.length; j++) {
                res += map.getOrDefault(-(nums3[i] + nums4[j]), 0);
            }
        }
        return res;
    }
}
```
