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
> </strong> The above elevation map (black section) is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped.
> </code></pre>
>
> **Example 2:**
>
> <pre><code>Input: height = [4,2,0,3,2,5]
> <strong>Output:
> </strong> 9
> </code></pre>

{% hint style="info" %}
最优解 双指针 由于每个位置的存水量由 min(left\_max, right\_max) - height\[i] 决定，我们可以用双指针代替 left\[] 和 right\[] 数组，节省空间。
{% endhint %}

```
class Solution {
    public int trap(int[] height) {
        if (height.length == 0) return 0;

        int left = 0, right = height.length - 1;
        int leftMax = 0, rightMax = 0, res = 0;

        while (left < right) {
            if (height[left] < height[right]) {
                if (height[left] >= leftMax) {
                    leftMax = height[left];
                } else {
                    res += leftMax - height[left];
                }
                left++;
            } else {
                if (height[right] >= rightMax) {
                    rightMax = height[right];
                } else {
                    res += rightMax - height[right];
                }
                right--;
            }
        }

        return res;
    }
}
```

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
每个位置都进入stack pre = stack.pop();

有上升墙壁的时候 pop出来的是height\[pre]是水的底部
{% endhint %}

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
