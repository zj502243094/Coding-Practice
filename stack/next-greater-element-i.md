# Next Greater Element I

[https://leetcode.com/problems/next-greater-element-i/](https://leetcode.com/problems/next-greater-element-i/)

> The **next greater element** of some element `x` in an array is the **first greater** element that is **to the right** of `x` in the same array.
>
> You are given two **distinct 0-indexed** integer arrays `nums1` and `nums2`, where `nums1` is a subset of `nums2`.
>
>
>
> **Example 1:**
>
> <pre><code>Input: nums1 = [4,1,2], nums2 = [1,3,4,2]
> <strong>Output:
> </strong> [-1,3,-1]
> <strong>Explanation:
> </strong> The next greater element for each value of nums1 is as follows:
> - 4 is underlined in nums2 = [1,3,4,2]. There is no next greater element, so the answer is -1.
> - 1 is underlined in nums2 = [1,3,4,2]. The next greater element is 3.
> - 2 is underlined in nums2 = [1,3,4,2]. There is no next greater element, so the answer is -1.</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: nums1 = [2,4], nums2 = [1,2,3,4]
> <strong>Output:
> </strong> [3,-1]</code></pre>

```
class Solution {
    public int[] nextGreaterElement(int[] nums1, int[] nums2) {
        Map<Integer, Integer> map = new HashMap<>();
        Stack<Integer> stack = new Stack<>();
        for (int i = nums2.length - 1; i >= 0; i--) {
            while (!stack.isEmpty() && nums2[i] >= stack.peek()) stack.pop();
            map.put(nums2[i], stack.isEmpty() ? -1 : stack.peek());
            stack.push(nums2[i]);
        }
        int[] res = new int[nums1.length];
        for (int i = 0; i < nums1.length; i++) {
            res[i] = map.get(nums1[i]);
        }
        return res;
    }
}
```
