# Remove K Digits

[https://leetcode.com/problems/remove-k-digits/](https://leetcode.com/problems/remove-k-digits/)

> Given string num representing a non-negative integer `num`, and an integer `k`, return _the smallest possible integer after removing_ `k` _digits from_ `num`.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: num = "1432219", k = 3
> <strong>Output:
> </strong> "1219"
> <strong>Explanation:
> </strong> Remove the three digits 4, 3, and 2 to form the new number 1219 which is the smallest.</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: num = "10200", k = 1
> <strong>Output:
> </strong> "200"
> <strong>Explanation:
> </strong> Remove the leading 1 and the number is 200. Note that the output must not contain leading zeroes.</code></pre>
>
> **Example 3:**
>
> <pre><code>Input: num = "10", k = 2
> <strong>Output:
> </strong> "0"
> <strong>Explanation:
> </strong> Remove all the digits from the number and it is left with nothing which is 0.</code></pre>

{% hint style="info" %}
生成最小递增序列，每次出现更小的值就将前面替换掉，替换次数不超过K
{% endhint %}

```
class Solution {
    public String removeKdigits(String num, int k) {
        Stack<Character> stack = new Stack<>();
        for (char c : num.toCharArray()) {
            while (!stack.isEmpty() && k > 0 && c < stack.peek()) {
                stack.pop();
                k--;
            }
            stack.push(c);
        }
        while (k-- > 0) stack.pop();
        StringBuilder sb = new StringBuilder();
        boolean zero = true;
        for (char c : stack) {
            if (c == '0' && zero) continue;
            else zero = false;
            sb.append(c - '0');
        }
        return sb.length() == 0 ? "0" : sb.toString();
    }
}
```
