# Basic Calculator

[https://leetcode.com/problems/basic-calculator/](https://leetcode.com/problems/basic-calculator/)

> Given a string `s` representing a valid expression, implement a basic calculator to evaluate it, and return _the result of the evaluation_.
>
> **Note:** You are **not** allowed to use any built-in function which evaluates strings as mathematical expressions, such as `eval()`.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: s = "1 + 1"
> <strong>Output: 2</strong></code></pre>
>
> **Example 2:**
>
> <pre><code>Input: s = " 2-1 + 2 "
> <strong>Output: 3</strong></code></pre>
>
> **Example 3:**
>
> <pre><code>Input: s = "(1+(4+5+2)-3)+(6+8)"
> <strong>Output: 23</strong></code></pre>

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
            if (c == '(') {
                num = calculate(s);
            }
            if (i >= s.length() || c == '+' || c == '-' || c == ')') {
                if (operator == '+') stack.push(num);
                else stack.push(-num);
                operator = c;
                num = 0;
            }
            if (c == ')') break;
        }
        int res = 0;
        while (!stack.isEmpty()) {
            res += stack.pop();
        }
        return res;
    }
}
```
