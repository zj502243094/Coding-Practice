# Minimum Add to Make Parentheses Valid

[https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/](https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/)

> A parentheses string is valid if and only if:
>
> * It is the empty string,
> * It can be written as `AB` (`A` concatenated with `B`), where `A` and `B` are valid strings, or
> * It can be written as `(A)`, where `A` is a valid string.
>
> You are given a parentheses string `s`. In one move, you can insert a parenthesis at any position of the string.
>
> * For example, if `s = "()))"`, you can insert an opening parenthesis to be `"(`**`(`**`)))"` or a closing parenthesis to be `"())`**`)`**`)"`.
>
> Return _the minimum number of moves required to make_ `s` _valid_.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: s = "())"
> <strong>Output: 1</strong></code></pre>
>
> **Example 2:**
>
> <pre><code>Input: s = "((("
> <strong>Output: 3</strong></code></pre>

{% hint style="info" %}
遇到左括号 补右括号+1&#x20;

遇到右括号 先减去要补的右括号 再加上需要补的左括号
{% endhint %}

```
class Solution {
    public int minAddToMakeValid(String s) {
        int left = 0, right = 0;
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == '(') {
                right++;
            }
            if (s.charAt(i) == ')') {
                if (right > 0) right--; 
                else left++;
            }
        }
        return left + right;
    }
}
```
