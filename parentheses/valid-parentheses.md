# Valid Parentheses

[https://leetcode.com/problems/valid-parentheses/](https://leetcode.com/problems/valid-parentheses/)

> Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.
>
> An input string is valid if:
>
> 1. Open brackets must be closed by the same type of brackets.
> 2. Open brackets must be closed in the correct order.
> 3. Every close bracket has a corresponding open bracket of the same type.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: s = "()"
> <strong>Output:
> </strong> true</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: s = "()[]{}"
> <strong>Output:
> </strong> true</code></pre>
>
> **Example 3:**
>
> <pre><code>Input: s = "(]"
> <strong>Output:
> </strong> false</code></pre>

```
class Solution {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();
        for(int i = 0; i < s.length(); i++){
            char a = s.charAt(i);
            if(a == '(' || a == '[' || a == '{') stack.push(a);
            else {
                if(stack.isEmpty()) return false;
                if(a == ')' && stack.pop() != '(') return false;
                if(a == ']' && stack.pop() != '[') return false;
                if(a == '}' && stack.pop() != '{') return false;
            }
        }
        return stack.isEmpty();
    }
}
```
