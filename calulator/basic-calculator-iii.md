# Basic Calculator III

[https://leetcode.com/problems/basic-calculator-iii/](https://leetcode.com/problems/basic-calculator-iii/)

> Implement a basic calculator to evaluate a simple expression string.
>
> The expression string contains only non-negative integers, `'+'`, `'-'`, `'*'`, `'/'` operators, and open `'('` and closing parentheses `')'`. The integer division should **truncate toward zero**.
>
> You may assume that the given expression is always valid. All intermediate results will be in the range of `[-231, 231 - 1]`.
>
> **Note:** You are not allowed to use any built-in function which evaluates strings as mathematical expressions, such as `eval()`.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: s = "1+1"
> <strong>Output:
> </strong> 2</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: s = "6-4/2"
> <strong>Output:
> </strong> 4</code></pre>
>
> **Example 3:**
>
> <pre><code>Input: s = "2*(5+5*2)/3+(6/2+8)"
> <strong>Output:
> </strong> 21</code></pre>

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
            if (i >= s.length() || c == '+' || c == '-' || c == '*' || c == '/' || c == ')') {
                if (operator == '+') stack.push(num);
                else if (operator == '-') stack.push(-num);
                else if (operator == '*') stack.push(stack.pop() * num);
                else if (operator == '/') stack.push(stack.pop() / num);
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
