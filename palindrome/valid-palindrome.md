# Valid Palindrome

[https://leetcode.com/problems/valid-palindrome/](https://leetcode.com/problems/valid-palindrome/)

有效回文串

> A phrase is a **palindrome** if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.
>
> Given a string `s`, return `true` _if it is a **palindrome**, or_ `false` _otherwise_.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: s = "A man, a plan, a canal: Panama"
> Output: true
> Explanation: "amanaplanacanalpanama" is a palindrome.
> ```
>
> **Example 2:**
>
> ```
> Input: s = "race a car"
> Output: false
> Explanation: "raceacar" is not a palindrome.
> ```
>
> **Example 3:**
>
> ```
> Input: s = " "
> Output: true
> Explanation: s is an empty string "" after removing non-alphanumeric characters.
> Since an empty string reads the same forward and backward, it is a palindrome.
> ```

{% hint style="info" %}
只记录字母 左端点小于右 l++ r--
{% endhint %}

```
class Solution {
    public boolean isPalindrome(String s) {
        if(s == null || s.length() == 0) return true;
        int l = 0, r = s.length() - 1;
        s = s.toLowerCase();
        while(l < r) {
            while(l < r && !Character.isLetterOrDigit(s.charAt(l))){
                l++;
            }
            while(l < r && !Character.isLetterOrDigit(s.charAt(r))){
                r--;
            }
            if(s.charAt(l) != s.charAt(r)) return false;
            l++;
            r--;
        }
        return true;
    }
}
```
