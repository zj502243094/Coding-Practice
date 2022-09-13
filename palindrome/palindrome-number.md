# Palindrome Number

[https://leetcode.com/problems/palindrome-number/](https://leetcode.com/problems/palindrome-number/)

> Given an integer `x`, return `true` if `x` is palindrome integer.
>
> An integer is a **palindrome** when it reads the same backward as forward.
>
> * For example, `121` is a palindrome while `123` is not.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: x = 121
> <strong>Output:
> </strong> true
> <strong>Explanation:
> </strong> 121 reads as 121 from left to right and from right to left.</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: x = -121
> <strong>Output:
> </strong> false
> <strong>Explanation:
> </strong> From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.</code></pre>
>
> **Example 3:**
>
> <pre><code>Input: x = 10
> <strong>Output:
> </strong> false
> <strong>Explanation:
> </strong> Reads 01 from right to left. Therefore it is not a palindrome.</code></pre>

```
class Solution {
    public boolean isPalindrome(int x) {
        int reverse = 0;
        int origin = x;
        while (x > 0) {
            reverse = reverse * 10 + x % 10;
            x /= 10;
        }
        return reverse == origin;
    }
}
```
