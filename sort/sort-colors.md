# Sort Colors

[https://leetcode.com/problems/sort-colors/](https://leetcode.com/problems/sort-colors/)

> Given an array `nums` with `n` objects colored red, white, or blue, sort them [**in-place**](https://en.wikipedia.org/wiki/In-place\_algorithm) **** so that objects of the same color are adjacent, with the colors in the order red, white, and blue.
>
> We will use the integers `0`, `1`, and `2` to represent the color red, white, and blue, respectively.
>
> You must solve this problem without using the library's sort function.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [2,0,2,1,1,0]
> Output: [0,0,1,1,2,2]
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [2,0,1]
> Output: [0,1,2]
> ```

{% hint style="info" %}
1. 先将 1 作为 pivot 然后 再讲 2  作为 pivot\
   &#x20;![](<../.gitbook/assets/image (5).png>)

2\. 记录 有几个0 几个1 几个2 然后 填上。

\

{% endhint %}
