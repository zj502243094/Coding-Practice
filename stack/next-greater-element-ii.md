# Next Greater Element II

[https://leetcode.com/problems/next-greater-element-ii/](https://leetcode.com/problems/next-greater-element-ii/)

> Given a circular integer array `nums` (i.e., the next element of `nums[nums.length - 1]` is `nums[0]`), return _the **next greater number** for every element in_ `nums`.
>
> The **next greater number** of a number `x` is the first greater number to its traversing-order next in the array, which means you could search circularly to find its next greater number. If it doesn't exist, return `-1` for this number.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: nums = [1,2,1]
> <strong>Output:
> </strong> [2,-1,2]
> Explanation: The first 1's next greater number is 2; 
> The number 2 can't find next greater number. 
> The second 1's next greater number needs to search circularly, which is also 2.
> </code></pre>
>
> **Example 2:**
>
> <pre><code>Input: nums = [1,2,3,4,3]
> <strong>Output:
> </strong> [2,3,4,-1,4]
> </code></pre>

{% hint style="info" %}
暴力方法就是 将数组copy一遍接到后面 然后再用第一题的方法
{% endhint %}

```
class Solution {
    public int[] nextGreaterElements(int[] nums) {
        int[] nums1 = new int[nums.length * 2];
        for (int i = 0; i < nums.length; i++) {
            nums1[i] = nums[i];
            nums1[i + nums.length] = nums[i];
        }
        int [] tmp = new int[nums1.length];
        Stack<Integer> stack = new Stack<>();
        for (int i = nums1.length - 1; i >= 0; i--) {
            while (!stack.isEmpty() && nums1[i] >= stack.peek()) stack.pop();
            tmp[i] = stack.isEmpty() ? -1 : stack.peek();
            stack.push(nums1[i]);
        }
        int [] res = new int[nums.length];
        for (int i = 0; i < nums.length; i++) {
            res[i] = tmp[i];
        }
        return res;
    }
}
```

```
class Solution {
    public int[] nextGreaterElements(int[] nums) {  
        int n = nums.length;
        int [] res = new int[n];
        Stack<Integer> stack = new Stack<>();
        for (int i = 2 * n - 1; i >= 0; i--) {
            while (!stack.isEmpty() && nums[i % n] >= stack.peek()) stack.pop();
            res[i % n] = stack.isEmpty() ? -1 : stack.peek();
            stack.push(nums[i % n]);
        }
        return res;
    }
}
```
