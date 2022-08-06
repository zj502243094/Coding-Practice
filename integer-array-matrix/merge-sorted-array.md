# Merge Sorted Array

[https://leetcode.com/problems/merge-sorted-array/](https://leetcode.com/problems/merge-sorted-array/)

> **Example 1:**
>
> <pre><code>Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
> <strong>Output: [1,2,2,3,5,6]
> </strong><strong>Explanation: The arrays we are merging are [1,2,3] and [2,5,6].
> </strong>The result of the merge is [1,2,2,3,5,6] with the underlined elements coming from nums1.</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: nums1 = [1], m = 1, nums2 = [], n = 0
> <strong>Output: [1]
> </strong><strong>Explanation: The arrays we are merging are [1] and [].
> </strong>The result of the merge is [1].</code></pre>
>
> **Example 3:**
>
> <pre><code>Input: nums1 = [0], m = 0, nums2 = [1], n = 1
> <strong>Output:[1]
> </strong><strong>Explanation: The arrays we are merging are [] and [1].
> </strong>The result of the merge is [1].
> Note that because m = 0, there are no elements in nums1. The 0 is only there to ensure the merge result can fit in nums1.</code></pre>

```
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int k = m + n - 1;
        int i = m - 1, j = n - 1;
        while (i >= 0 && j >= 0) {
            if (nums1[i] >= nums2[j]) {
                nums1[k--] = nums1[i--];
            } else {
                nums1[k--] = nums2[j--];
            }
        }
        while (j >= 0) {
            nums1[k--] = nums2[j--];
        }
    }
}
```
