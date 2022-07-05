# Reverse String / Reverse String II

[https://leetcode.com/problems/reverse-string/](https://leetcode.com/problems/reverse-string/)

> Write a function that reverses a string. The input string is given as an array of characters `s`.
>
> You must do this by modifying the input array [in-place](https://en.wikipedia.org/wiki/In-place\_algorithm) with `O(1)` extra memory.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: s = ["h","e","l","l","o"]
> Output: ["o","l","l","e","h"]
> ```
>
> **Example 2:**
>
> ```
> Input: s = ["H","a","n","n","a","h"]
> Output: ["h","a","n","n","a","H"]
> ```

```
class Solution {
    public void reverseString(char[] s) {
        int i = 0;
        int j = s.length - 1;
        while(i <= j){
            char tmp = s[i];
            s[i] = s[j];
            s[j] = tmp;
            i++;
            j--;
        }
    }
}
```



[https://leetcode.com/problems/reverse-string-ii/](https://leetcode.com/problems/reverse-string-ii/)

每2k个数 翻转第k个字母

> Given a string `s` and an integer `k`, reverse the first `k` characters for every `2k` characters counting from the start of the string.
>
> If there are fewer than `k` characters left, reverse all of them. If there are less than `2k` but greater than or equal to `k` characters, then reverse the first `k` characters and leave the other as original.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: s = "abcdefg", k = 2
> Output: "bacdfeg"
> ```
>
> **Example 2:**
>
> ```
> Input: s = "abcd", k = 2
> Output: "bacd"
> ```

```
class Solution {
    public String reverseStr(String s, int k) {
        char[] a = s.toCharArray();
        for (int i = 0; i < a.length; i += 2 * k) {
            int l = i, r = Math.min(i + k - 1, a.length - 1);
            while(l < r) {
                char tmp = a[l];
                a[l] = a[r];
                a[r] = tmp;
                l++;
                r--;
            }
        }
        return new String(a);
    }
}
```
