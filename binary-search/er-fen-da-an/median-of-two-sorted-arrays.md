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

使用双指针分别对两个数组遍历，比较两个指针下的元素大小，每次移动更小的指针，通过移动次数确定中位数的位置。
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

{% hint style="info" %}
O ( l o g ( m + n ) ) / O ( 1 )
{% endhint %}

```
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int n = nums1.length + nums2.length;
        if (n % 2 == 0) {
            return (
                findKth(nums1, 0, nums2, 0, n / 2) + 
                findKth(nums1, 0, nums2, 0, n / 2 + 1)
            ) / 2.0; 
        }
        return findKth(nums1, 0, nums2, 0, n / 2 + 1);
    }
    private double findKth(int[] nums1, int s1, int[] nums2, int s2, int k) {
        if (s1 > nums1.length - 1) return nums2[s2 + k - 1]; 
        if (s2 > nums2.length - 1) return nums1[s1 + k - 1];
        if (k == 1) return Math.min(nums1[s1], nums2[s2]);
        int mid1 = Integer.MAX_VALUE;
        int mid2 = Integer.MAX_VALUE;
        if (s1 + k / 2 - 1 < nums1.length) mid1 = nums1[s1 + k / 2 - 1];
        if (s2 + k / 2 - 1 < nums2.length) mid2 = nums2[s2 + k / 2 - 1];
        if (mid1 < mid2) {
            return findKth(nums1, s1 + k / 2, nums2, s2, k - k / 2);
        } else {
            return findKth(nums1, s1, nums2, s2 + k / 2, k - k / 2);
        }
    }
}
```
