# Daily Temperatures

[https://leetcode.com/problems/daily-temperatures/](https://leetcode.com/problems/daily-temperatures/)

找到下一个更暖的一天

> Given an array of integers `temperatures` represents the daily temperatures, return _an array_ `answer` _such that_ `answer[i]` _is the number of days you have to wait after the_ `ith` _day to get a warmer temperature_. If there is no future day for which this is possible, keep `answer[i] == 0` instead.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: temperatures = [73,74,75,71,69,72,76,73]
> <strong>Output:
> </strong> [1,1,4,2,1,1,0,0]</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: temperatures = [30,40,50,60]
> <strong>Output:
> </strong> [1,1,1,0]</code></pre>
>
> **Example 3:**
>
> <pre><code>Input: temperatures = [30,60,90]
> <strong>Output:
> </strong> [1,1,0]</code></pre>

```
class Solution {
    public int[] dailyTemperatures(int[] temp) {
        int n = temp.length;
        int[] res = new int[n];
        Stack<Integer> stack = new Stack<>();
        for (int i = n - 1; i >= 0; i--) {
            while (!stack.isEmpty() && temp[i] >= temp[stack.peek()]) stack.pop();
            res[i] = stack.isEmpty() ? 0 : stack.peek() - i;
            stack.push(i);
        }
        return res;
    }
}
```
