# Score of Parentheses

[https://leetcode.com/problems/score-of-parentheses/](https://leetcode.com/problems/score-of-parentheses/)

> Given a balanced parentheses string `s`, return _the **score** of the string_.
>
> The **score** of a balanced parentheses string is based on the following rule:
>
> * `"()"` has score `1`.
> * `AB` has score `A + B`, where `A` and `B` are balanced parentheses strings.
> * `(A)` has score `2 * A`, where `A` is a balanced parentheses string.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: s = "()"
> <strong>Output:
> </strong> 1</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: s = "(())"
> <strong>Output:
> </strong> 2</code></pre>
>
> **Example 3:**
>
> <pre><code>Input: s = "()()"
> <strong>Output:
> </strong> 2</code></pre>

{% hint style="info" %}
stack 存前面一层的数字 闭括号要前面的数组 \* 2 然后再和更前面的相加
{% endhint %}

```
class Solution {
    public int scoreOfParentheses(String s) {
        Stack<Integer> stack = new Stack<>();
        int cur = 0;
        for (char c : s.toCharArray()) {
            if (c == '(') {
                stack.push(cur);
                cur = 0;
            } else {
                cur = stack.pop() + Math.max(cur * 2, 1);
            }
        }
        return cur;
    }
}
```
