# Median of Two Sorted Arrays

[https://leetcode.com/problems/median-of-two-sorted-arrays/](https://leetcode.com/problems/median-of-two-sorted-arrays/)

> Given two sorted arrays `nums1` and `nums2` of size `m` and `n` respectively, return **the median** of the two sorted arrays.
>
> The overall run time complexity should be `O(log (m+n))`.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: nums1 = [1,3], nums2 = [2]
> <strong>Output: 2.00000
> </strong><strong>Explanation: merged array = [1,2,3] and median is 2.</strong></code></pre>
>
> **Example 2:**
>
> <pre><code>Input: nums1 = [1,2], nums2 = [3,4]
> <strong>Output: 2.50000
> </strong><strong>Explanation: merged array = [1,2,3,4] and median is (2 + 3) / 2 = 2.5.</strong></code></pre>

{% hint style="info" %}
O ( m + n )  / O ( 1 )
{% endhint %}

```
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int m = nums1.length, n = nums2.length;
        int p1 = 0, p2 = 0;
        int left = 0, right = 0;
        for (int i = 0; i < (m + n) / 2 + 1; i++) {
            left = right;
            if (p1 >= m || p2 < n && nums1[p1] > nums2[p2]) {
                right = nums2[p2++];
            } else {
                right = nums1[p1++];
            }
        }
        return (m + n) % 2 == 0 ? (left + right) / 2.0 : right;
    }
}
```
