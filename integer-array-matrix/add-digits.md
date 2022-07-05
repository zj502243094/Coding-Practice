# Add Digits

[https://leetcode.com/problems/add-digits/](https://leetcode.com/problems/add-digits/)

所有位数相加 直到加到个位数

> Given an integer `num`, repeatedly add all its digits until the result has only one digit, and return it.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: num = 38
> Output: 2
> Explanation: The process is
> 38 --> 3 + 8 --> 11
> 11 --> 1 + 1 --> 2 
> Since 2 has only one digit, return it.
> ```
>
> **Example 2:**
>
> ```
> Input: num = 0
> Output: 0
> ```

{% hint style="info" %}
如果当前数 >= 10 就 %10得到个位数 然后 / 10 直到num=0&#x20;
{% endhint %}

```
class Solution {
    public int addDigits(int num) {
        while(num >= 10) {
            int temp = 0;
            while(num > 0){
                temp += num % 10;
                num = num / 10;
            } 
            num = temp;
        }
        return num;
    }
}
```
