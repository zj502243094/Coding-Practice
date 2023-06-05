# Next Permutation

[https://leetcode.com/problems/next-permutation/description/](https://leetcode.com/problems/next-permutation/description/)\


> A **permutation** of an array of integers is an arrangement of its members into a sequence or linear order.
>
> * For example, for `arr = [1,2,3]`, the following are all the permutations of `arr`: `[1,2,3], [1,3,2], [2, 1, 3], [2, 3, 1], [3,1,2], [3,2,1]`.
>
> The **next permutation** of an array of integers is the next lexicographically greater permutation of its integer. More formally, if all the permutations of the array are sorted in one container according to their lexicographical order, then the **next permutation** of that array is the permutation that follows it in the sorted container. If such arrangement is not possible, the array must be rearranged as the lowest possible order (i.e., sorted in ascending order).
>
> * For example, the next permutation of `arr = [1,2,3]` is `[1,3,2]`.
> * Similarly, the next permutation of `arr = [2,3,1]` is `[3,1,2]`.
> * While the next permutation of `arr = [3,2,1]` is `[1,2,3]` because `[3,2,1]` does not have a lexicographical larger rearrangement.
>
> Given an array of integers `nums`, _find the next permutation of_ `nums`.
>
> The replacement must be [**in place**](http://en.wikipedia.org/wiki/In-place\_algorithm) and use only constant extra memory.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code><strong>Input: nums = [1,2,3]
> </strong><strong>Output: [1,3,2]
> </strong></code></pre>
>
> **Example 2:**
>
> <pre><code><strong>Input: nums = [3,2,1]
> </strong><strong>Output: [1,2,3]
> </strong></code></pre>
>
> **Example 3:**
>
> <pre><code><strong>Input: nums = [1,1,5]
> </strong><strong>Output: [1,5,1]
> </strong></code></pre>

```
class Solution {
    public void nextPermutation(int[] nums) {
        // Step 1: Find the first pair (i, i+1) from the right such that nums[i] < nums[i+1]
        int i = nums.length - 2;
        while (i >= 0 && nums[i] >= nums[i + 1]) {
            i--;
        }

        if (i >= 0) {
            // Step 2: Find the first element j from the right such that nums[j] > nums[i]
            int j = nums.length - 1;
            while (j > i && nums[j] <= nums[i]) {
                j--;
            }

            // Step 3: Swap nums[i] with nums[j]
            swap(nums, i, j);
        }

        // Step 4: Reverse the subarray starting from index i+1 till the end of the array
        reverse(nums, i + 1);
    }
    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }

    private void reverse(int[] nums, int start) {
        int i = start;
        int j = nums.length - 1;
        while (i < j) {
            swap(nums, i, j);
            i++;
            j--;
        }
    }
}
```
