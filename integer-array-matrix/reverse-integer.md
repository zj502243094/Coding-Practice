# Reverse Integer

[https://leetcode.com/problems/reverse-integer/](https://leetcode.com/problems/reverse-integer/)

> Given a signed 32-bit integer `x`, return `x` _with its digits reversed_. If reversing `x` causes the value to go outside the signed 32-bit integer range `[-231, 231 - 1]`, then return `0`.
>
> **Assume the environment does not allow you to store 64-bit integers (signed or unsigned).**
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: x = 123
> Output: 321
> ```
>
> **Example 2:**
>
> ```
> Input: x = -123
> Output: -321
> ```
>
> **Example 3:**
>
> ```
> Input: x = 120
> Output: 21
> ```

{% hint style="info" %}
X % 10 取个位 然后\*10 加上 x / 10后的新数
{% endhint %}

```
class Solution {
    public int reverse(int x) {
        long res = 0;
        while (x != 0){
            res = res * 10 + x % 10;
            x = x / 10;
        }
        if (res < Integer.MIN_VALUE || res > Integer.MAX_VALUE) {
            return 0;
        } else {
            return (int)res;
        }
    }
}
```
