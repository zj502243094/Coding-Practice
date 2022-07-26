# Evaluate Reverse Polish Notation

[https://leetcode.com/problems/evaluate-reverse-polish-notation/](https://leetcode.com/problems/evaluate-reverse-polish-notation/)

每次将运算符前面两个数字进行运算 然后 压回栈 继续运算

> Evaluate the value of an arithmetic expression in [Reverse Polish Notation](http://en.wikipedia.org/wiki/Reverse\_Polish\_notation).
>
> Valid operators are `+`, `-`, `*`, and `/`. Each operand may be an integer or another expression.
>
> **Note** that division between two integers should truncate toward zero.
>
> It is guaranteed that the given RPN expression is always valid. That means the expression would always evaluate to a result, and there will not be any division by zero operation.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: tokens = ["2","1","+","3","*"]
> Output: 9
> Explanation: ((2 + 1) * 3) = 9
> ```
>
> **Example 2:**
>
> ```
> Input: tokens = ["4","13","5","/","+"]
> Output: 6
> Explanation: (4 + (13 / 5)) = 6
> ```
>
> **Example 3:**
>
> ```
> Input: tokens = ["10","6","9","3","+","-11","*","/","*","17","+","5","+"]
> Output: 22
> Explanation: ((10 * (6 / ((9 + 3) * -11))) + 17) + 5
> = ((10 * (6 / (12 * -11))) + 17) + 5
> = ((10 * (6 / -132)) + 17) + 5
> = ((10 * 0) + 17) + 5
> = (0 + 17) + 5
> = 17 + 5
> = 22
> ```

```
class Solution {
    public int evalRPN(String[] tokens) {
        Stack<Integer> s = new Stack();
        String operators = "+-*/";
        for(String token : tokens) {
            if(!operators.contains(token)) {
                s.push(Integer.valueOf(token));
            } else {
                int a = s.pop();
                int b = s.pop();
                int res;
                if(token.equals("+")){
                    res = a + b;
                    s.push(res);
                }
                if(token.equals("-")){
                    res = b - a;
                    s.push(res);
                }
                if(token.equals("*")){
                    res = a * b;
                    s.push(res);
                }
                if(token.equals("/")){
                    res = b / a;
                    s.push(res);
                }
            }
        }
        return s.pop();
    }
}
```
