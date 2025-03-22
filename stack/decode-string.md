# Decode String

[https://leetcode.com/problems/decode-string/](https://leetcode.com/problems/decode-string/)

> Given an encoded string, return its decoded string.
>
> The encoding rule is: `k[encoded_string]`, where the `encoded_string` inside the square brackets is being repeated exactly `k` times. Note that `k` is guaranteed to be a positive integer.
>
> You may assume that the input string is always valid; there are no extra white spaces, square brackets are well-formed, etc. Furthermore, you may assume that the original data does not contain any digits and that digits are only for those repeat numbers, `k`. For example, there will not be input like `3a` or `2[4]`.
>
> The test cases are generated so that the length of the output will never exceed `105`.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code><strong>Input: s = "3[a]2[bc]"
> </strong><strong>Output: "aaabcbc"
> </strong></code></pre>
>
> **Example 2:**
>
> <pre><code><strong>Input: s = "3[a2[c]]"
> </strong><strong>Output: "accaccacc"
> </strong></code></pre>
>
> **Example 3:**
>
> <pre><code><strong>Input: s = "2[abc]3[cd]ef"
> </strong><strong>Output: "abcabccdcdcdef"
> </strong></code></pre>

<pre><code><strong>class Solution {    
</strong><strong>    public String decodeString(String s) {
</strong>        Stack&#x3C;Integer> countStack = new Stack&#x3C;>();
        Stack&#x3C;StringBuilder> stringStack = new Stack&#x3C;>();
        StringBuilder currentStr = new StringBuilder();
        int num = 0;

        for (char c : s.toCharArray()) {
            if (Character.isDigit(c)){
                num = num * 10 + (c - '0');
            } else if (c == '[') {
                countStack.push(num);
                stringStack.push(currentStr);
                currentStr = new StringBuilder();
                num = 0;
            } else if (c == ']') {
                int repeatTimes = countStack.pop();
                StringBuilder decodeString = stringStack.pop();
                decodeString.append(String.valueOf(currentStr).repeat(repeatTimes));
                currentStr = decodeString;
            } else {
                currentStr.append(c);
            }
        }
        return currentStr.toString();
    }
}
</code></pre>
