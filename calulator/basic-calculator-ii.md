# Basic Calculator II

[https://leetcode.com/problems/basic-calculator-ii/](https://leetcode.com/problems/basic-calculator-ii/)

> Given a string `s` which represents an expression, _evaluate this expression and return its value_.&#x20;
>
> The integer division should truncate toward zero.
>
> You may assume that the given expression is always valid. All intermediate results will be in the range of `[-231, 231 - 1]`.
>
> **Note:** You are not allowed to use any built-in function which evaluates strings as mathematical expressions, such as `eval()`.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: s = "3+2*2"
> <strong>Output: 7</strong></code></pre>
>
> **Example 2:**
>
> <pre><code>Input: s = " 3/2 "
> <strong>Output: 1</strong></code></pre>
>
> **Example 3:**
>
> <pre><code>Input: s = " 3+5 / 2 "
> <strong>Output: 5</strong></code></pre>

```
class Solution {
    int i = 0;
    public int calculate(String s) {
        Stack<Integer> stack = new Stack<>();
        char operator = '+';
        int num = 0;
        while (i < s.length()) {
            char c = s.charAt(i++);
            if (c >= '0' && c <= '9') {
                num = num * 10 + (c - '0');
            }
            if (i >= s.length() || c == '+' || c == '-' || c == '*' || c == '/') {
                if (operator == '+') stack.push(num);
                else if (operator == '-') stack.push(-num);
                else if (operator == '*') stack.push(stack.pop() * num);
                else if (operator == '/') stack.push(stack.pop() / num);
                operator = c;
                num = 0;
            }
        }
        int res = 0;
        while (!stack.isEmpty()) {
            res += stack.pop();
        }
        return res;
    }
}
```
