# Sqrt(x) / Sqrt(x) II

开根号

[https://leetcode.com/problems/sqrtx/](https://leetcode.com/problems/sqrtx/)

> Given a non-negative integer `x`, compute and return _the square root of_ `x`.
>
> Since the return type is an integer, the decimal digits are **truncated**, and only **the integer part** of the result is returned.
>
> **Note:** You are not allowed to use any built-in exponent function or operator, such as `pow(x, 0.5)` or `x ** 0.5`.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: x = 4
> Output: 2
> ```
>
> **Example 2:**
>
> ```
> Input: x = 8
> Output: 2
> Explanation: The square root of 8 is 2.82842..., and since the decimal part is truncated, 2 is returned.
> ```

```
class Solution {
    public int mySqrt(int x) {
        if(x == 0) return 0;
        int left = 1, right = x;
        while(left + 1 < right){
            int mid = (right - left) / 2 + left;
            if(mid <= x / mid){
                left = mid;
            }else{
                right = mid;
            }
        }
        if(right == x / right) return right;
        return left;
    }
}
```

\
[https://www.lintcode.com/problem/586/](https://www.lintcode.com/problem/586/)\
