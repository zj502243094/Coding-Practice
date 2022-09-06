# Minimum Remove to Make Valid Parentheses

[https://leetcode.com/problems/minimum-remove-to-make-valid-parentheses/](https://leetcode.com/problems/minimum-remove-to-make-valid-parentheses/)

> Given a string s of `'('` , `')'` and lowercase English characters.
>
> Your task is to remove the minimum number of parentheses ( `'('` or `')'`, in any positions ) so that the resulting _parentheses string_ is valid and return **any** valid string.
>
> Formally, a _parentheses string_ is valid if and only if:
>
> * It is the empty string, contains only lowercase characters, or
> * It can be written as `AB` (`A` concatenated with `B`), where `A` and `B` are valid strings, or
> * It can be written as `(A)`, where `A` is a valid string.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: s = "lee(t(c)o)de)"
> <strong>Output:
> </strong> "lee(t(c)o)de"
> <strong>Explanation:
> </strong> "lee(t(co)de)" , "lee(t(c)ode)" would also be accepted.</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: s = "a)b(c)d"
> <strong>Output:
> </strong> "ab(c)d"</code></pre>
>
> **Example 3:**
>
> <pre><code>Input: s = "))(("
> <strong>Output:
> </strong> ""
> <strong>Explanation:
> </strong> An empty string is also valid.</code></pre>

{% hint style="info" %}
set存储invalid括号位置&#x20;

遇到 左括号加到 stack里面 遇到右括号从stack pop

如果stack 是空的 且 遇到右括号 就是invalid 或者 S 走完了 Stack不是空的 也是invalid
{% endhint %}

```
class Solution {
    public String minRemoveToMakeValid(String s) {
        Set<Integer> set = new HashSet<>();
        Stack<Integer> stack = new Stack<>();
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == '(') stack.push(i);
            else if (s.charAt(i) == ')') {
                if (stack.isEmpty()) set.add(i);
                else stack.pop();
            }
        }
        while (!stack.isEmpty()) set.add(stack.pop());
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < s.length(); i++) {
            if (!set.contains(i)) {
                sb.append(s.charAt(i));
            }
        }
        return sb.toString();
    }
}
```

```
class Solution {
    public String minRemoveToMakeValid(String s) {
        StringBuilder sb = new StringBuilder();
        int balance = 0;
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            if (c == '(') balance++;
            if (c == ')') {
                if (balance == 0) continue;
                balance--;
            }
            sb.append(c);
        }
        StringBuilder res = new StringBuilder();
        balance = 0;
        for (int i = sb.length() - 1; i >= 0; i--) {
            char c = sb.charAt(i);
            if (c == ')') balance++;
            if (c == '(') {
                if (balance == 0) continue;
                balance--;
            }
            res.append(c);
        }
        return res.reverse().toString();
    }
}
```
