# Trapping Rain Water

[https://leetcode.com/problems/trapping-rain-water/](https://leetcode.com/problems/trapping-rain-water/)

> Given `n` non-negative integers representing an elevation map where the width of each bar is `1`, compute how much water it can trap after raining.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2018/10/22/rainwatertrap.png)
>
> <pre><code>Input: height = [0,1,0,2,1,0,1,3,2,1,2,1]
> <strong>Output:
> </strong> 6
> <strong>Explanation:
> </strong> The above elevation map (black section) is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped.</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: height = [4,2,0,3,2,5]
> <strong>Output:
> </strong> 9</code></pre>

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

```
class Solution {
    public int trap(int[] height) {
        Stack<Integer> stack = new Stack<>();
        int res = 0;
        int n = height.length;
        for (int i = 0; i < n; i++) {
            while (!stack.isEmpty() && height[i] > height[stack.peek()]) {
                int pre = stack.pop();
                if (stack.isEmpty()) break;
                int minHeight = Math.min(height[stack.peek()], height[i]);
                res += (minHeight - height[pre]) * (i - stack.peek() - 1);
            }
            stack.push(i);
        }
        return res;
    }
}
```
