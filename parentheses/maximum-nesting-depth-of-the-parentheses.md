# Maximum Nesting Depth of the Parentheses

[https://leetcode.com/problems/maximum-nesting-depth-of-the-parentheses/](https://leetcode.com/problems/maximum-nesting-depth-of-the-parentheses/)

> A string is a **valid parentheses string** (denoted **VPS**) if it meets one of the following:
>
> * It is an empty string `""`, or a single character not equal to `"("` or `")"`,
> * It can be written as `AB` (`A` concatenated with `B`), where `A` and `B` are **VPS**'s, or
> * It can be written as `(A)`, where `A` is a **VPS**.
>
> We can similarly define the **nesting depth** `depth(S)` of any VPS `S` as follows:
>
> * `depth("") = 0`
> * `depth(C) = 0`, where `C` is a string with a single character not equal to `"("` or `")"`.
> * `depth(A + B) = max(depth(A), depth(B))`, where `A` and `B` are **VPS**'s.
> * `depth("(" + A + ")") = 1 + depth(A)`, where `A` is a **VPS**.
>
> For example, `""`, `"()()"`, and `"()(()())"` are **VPS**'s (with nesting depths 0, 1, and 2), and `")("` and `"(()"` are not **VPS**'s.
>
> Given a **VPS** represented as string `s`, return _the **nesting depth** of_ `s`.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: s = "(1+(2*3)+((8)/4))+1"
> <strong>Output: 3
> </strong><strong>Explanation:
> </strong> Digit 8 is inside of 3 nested parentheses in the string.</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: s = "(1)+((2))+(((3)))"
> <strong>Output: 3</strong></code></pre>

{% hint style="info" %}
rolling state&#x20;

忽略 数组 和字母 遇到 左括号 +1 右括号-1&#x20;

深度 就是最大括号
{% endhint %}

```
class Solution {
    public int maxDepth(String s) {
        int res = 0;
        int count = 0;
        for (char c : s.toCharArray()) {
            if (c == '(') {
                count++;
            } else if (c == ')') {
                count--;
            }
            res = Math.max(res, count);
        }
        return res;
    }
}
```
