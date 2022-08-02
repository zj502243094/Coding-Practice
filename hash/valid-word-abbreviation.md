# Valid Word Abbreviation

[https://leetcode.com/problems/valid-word-abbreviation/](https://leetcode.com/problems/valid-word-abbreviation/)

检查 一个字符 缩写 缩的正确性

> A string can be **abbreviated** by replacing any number of **non-adjacent**, **non-empty** substrings with their lengths. The lengths **should not** have leading zeros.
>
> For example, a string such as `"substitution"` could be abbreviated as (but not limited to):
>
> * `"s10n"` (`"s ubstitutio n"`)
> * `"sub4u4"` (`"sub stit u tion"`)
> * `"12"` (`"substitution"`)
> * `"su3i1u2on"` (`"su bst i t u ti on"`)
> * `"substitution"` (no substrings replaced)
>
> The following are **not valid** abbreviations:
>
> * `"s55n"` (`"s ubsti tutio n"`, the replaced substrings are adjacent)
> * `"s010n"` (has leading zeros)
> * `"s0ubstitution"` (replaces an empty substring)
>
> Given a string `word` and an abbreviation `abbr`, return _whether the string **matches** the given abbreviation_.
>
> A **substring** is a contiguous **non-empty** sequence of characters within a string.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: word = "internationalization", abbr = "i12iz4n"
> Output: true
> ```

{% hint style="info" %}
同时遍历 word 和 abbr 如果 字符相同 就继续向后

如果abbr 中字符是数字 跳过的数字后 word 和 abbr相同 （每次位数 \* 10 ） 为真

最后确保i j 走完了
{% endhint %}

```
class Solution {
    public boolean validWordAbbreviation(String word, String abbr) {
        if (word == null || abbr == null) return false;
        int i = 0, j = 0;
        while (i < word.length() && j < abbr.length()) {
            char c1 = word.charAt(i);
            char c2 = abbr.charAt(j);
            
            if (c1 == c2) {
                i++;
                j++;
            } else if (Character.isDigit(c2) && c2 != '0') {
                int num = 0;
                while (j < abbr.length() && Character.isDigit(abbr.charAt(j))) {
                    num = num * 10 + (abbr.charAt(j) - '0');
                    j++;
                }
                i += num;
            } else {
                return false;
            }
        }
        return i == word.length() && j == abbr.length();
    }
}
```
