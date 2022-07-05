# Reverse Words in a String II

[https://leetcode.com/problems/reverse-words-in-a-string-ii/](https://leetcode.com/problems/reverse-words-in-a-string-ii/)

> Given a character array `s`, reverse the order of the **words**.
>
> A **word** is defined as a sequence of non-space characters. The **words** in `s` will be separated by a single space.
>
> Your code must solve the problem **in-place,** i.e. without allocating extra space.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: s = ["t","h","e"," ","s","k","y"," ","i","s"," ","b","l","u","e"]
> Output: ["b","l","u","e"," ","i","s"," ","s","k","y"," ","t","h","e"]
> ```
>
> **Example 2:**
>
> ```
> Input: s = ["a"]
> Output: ["a"]
> ```

{% hint style="info" %}
讲整个char翻转然后 以空格为单位 翻转单词
{% endhint %}

```
class Solution {
    public void reverseWords(char[] s) {
        reverse(s, 0, s.length - 1);
        int l = 0, r = 0;
        
        while(r < s.length){
            l = r;
            while(r < s.length && s[r] != ' ') r++;
            reverse(s, l, r - 1);
            r++;
        }
    }
    private void reverse(char[] s, int i, int j){
        while(i < j){
            char tmp = s[i];
            s[i] = s[j];
            s[j] = tmp;
            i++;
            j--;
        }
    }
}
```
