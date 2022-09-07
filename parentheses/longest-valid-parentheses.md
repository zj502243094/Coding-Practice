# Longest Valid Parentheses

[https://leetcode.com/problems/longest-valid-parentheses/](https://leetcode.com/problems/longest-valid-parentheses/)

> Given a string containing just the characters `'('` and `')'`, find the length of the longest valid (well-formed) parentheses substring.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: s = "(()"
> <strong>Output:
> </strong> 2
> <strong>Explanation:
> </strong> The longest valid parentheses substring is "()".</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: s = ")()())"
> <strong>Output:
> </strong> 4
> <strong>Explanation:
> </strong> The longest valid parentheses substring is "()()".</code></pre>
>
> **Example 3:**
>
> <pre><code>Input: s = ""
> <strong>Output:
> </strong> 0</code></pre>

{% hint style="info" %}
stack 存的都是valid的位置  遇到右括号 先pop出左括号 再求长度![](<../.gitbook/assets/image (16).png>)
{% endhint %}

```
class Solution {
    public int longestValidParentheses(String s) {
        int res = 0;
        Stack<Integer> stack = new Stack<>();
        stack.push(-1);
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == '(') stack.push(i);
            else {
                stack.pop();
                if (stack.isEmpty()) stack.push(i);
                else res = Math.max(res, i - stack.peek());
            }
        }
        return res;
    }
}
```

{% hint style="info" %}
two pass 先从左往右 找一遍最大值 再从右往左找一遍
{% endhint %}

```
class Solution {
    public int longestValidParentheses(String s) {
        int cntl = 0, cntr = 0, res = 0;
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            if (c == '(') cntl++;
            else cntr++;
            if (cntl == cntr) {
                res = Math.max(res, cntl * 2);
            } else if (cntr > cntl) {
                cntl = cntr = 0;
            }
        }
        cntl = cntr = 0;
        for (int i = s.length() - 1; i >= 0; i--) {
            char c = s.charAt(i);
            if (c == '(') cntl++;
            else cntr++;
            if (cntl == cntr) {
                res = Math.max(res, cntl * 2);
            } else if (cntl > cntr) {
                cntl = cntr = 0;
            }
        }
        return res;
    }
}
```
