# Largest Rectangle in Histogram

[https://leetcode.com/problems/largest-rectangle-in-histogram/](https://leetcode.com/problems/largest-rectangle-in-histogram/)

> Given an array of integers `heights` representing the histogram's bar height where the width of each bar is `1`, return _the area of the largest rectangle in the histogram_.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/01/04/histogram.jpg)
>
> ```
> Input: heights = [2,1,5,6,2,3]
> Output: 10
> Explanation: The above is a histogram where width of each bar is 1.
> The largest rectangle is shown in the red area, which has an area = 10 units.
> ```
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2021/01/04/histogram-1.jpg)
>
> ```
> Input: heights = [2,4]
> Output: 4
> ```

{% hint style="info" %}
穷举 柱子 分别找到左右比本身矮的柱子\
当柱子 i j  i < j && h\[i] >= h\[j] i 不可能是 后面柱子的左边界  所以候选左边界list 只能是单调递增的（因为 不满足这个性质的柱子 会被删掉不可能作为左边界）\
![](<../.gitbook/assets/image (10) (1).png>)\
![](<../.gitbook/assets/image (13).png>)\
同样方法可以求出右边界 就可以求出 cur 柱子 的面积\
每个 柱子 在每次循环中 进入 弹出各一次 所以 time O（n）\
\
首先 实现这个左边界单调栈 将柱子依次压入栈中 当栈中柱子最高高度大于当前要压入栈中的cur 就将栈中最大值pop出  对于POP出的柱子 他的所对应的最大面积 本身高度和将其弹出的柱子位置 i 相乘&#x20;

然后将单调栈弹空 求单调栈中每个柱子对应最大面积 &#x20;
{% endhint %}

```
class Solution {
    public int largestRectangleArea(int[] heights) {
        if(heights == null || heights.length == 0) return 0;
        int res = 0;
        Stack<Integer> stack = new Stack();
        
        for(int i = 0; i <= heights.length; i++){
            int cur = (i == heights.length) ? -1 : heights[i];
            while(!stack.isEmpty() && heights[stack.peek()] >= cur){
                int h = heights[stack.pop()];
                int w = stack.isEmpty() ? i : i - stack.peek() - 1;
                res = Math.max(h * w, res);
            }
            stack.push(i);
        }
        return res;
    }
}
```
