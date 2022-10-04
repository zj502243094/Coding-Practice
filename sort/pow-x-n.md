# Pow(x, n)

[https://leetcode.com/problems/powx-n/](https://leetcode.com/problems/powx-n/)

> Implement [pow(x, n)](http://www.cplusplus.com/reference/valarray/pow/), which calculates `x` raised to the power `n` (i.e., `xn`).
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: x = 2.00000, n = 10
> <strong>Output:
> </strong> 1024.00000</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: x = 2.10000, n = 3
> <strong>Output:
> </strong> 9.26100</code></pre>
>
> **Example 3:**
>
> <pre><code>Input: x = 2.00000, n = -2
> <strong>Output:
> </strong> 0.25000
> <strong>Explanation:
> </strong> 2-2 = 1/22 = 1/4 = 0.25</code></pre>

```
class Solution {
    public double myPow(double x, int n) {
        if (x == 0 || x == 1) return x;
        if (n < 0) return 1 / pow(x, -n);
        return pow(x, n);
    }
    private double pow(double x, int n) {
        if (n == 0) return 1;
        double y = pow(x, n / 2);
        if (n % 2 == 0) return y * y;
        else return y * y * x;
    }
}
```
