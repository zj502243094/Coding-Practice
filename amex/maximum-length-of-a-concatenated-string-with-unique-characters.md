# Maximum Length of a Concatenated String with Unique Characters

[https://leetcode.com/problems/maximum-length-of-a-concatenated-string-with-unique-characters/](https://leetcode.com/problems/maximum-length-of-a-concatenated-string-with-unique-characters/)

组成最长不重复字符串的 长度

> You are given an array of strings `arr`. A string `s` is formed by the **concatenation** of a **subsequence** of `arr` that has **unique characters**.
>
> Return _the **maximum** possible length_ of `s`.
>
> A **subsequence** is an array that can be derived from another array by deleting some or no elements without changing the order of the remaining elements.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: arr = ["un","iq","ue"]
> <strong>Output:4
> </strong><strong>Explanation:
> </strong> All the valid concatenations are:
> - ""
> - "un"
> - "iq"
> - "ue"
> - "uniq" ("un" + "iq")
> - "ique" ("iq" + "ue")
> Maximum length is 4.</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: arr = ["cha","r","act","ers"]
> <strong>Output: 6
> </strong><strong>Explanation:
> </strong> Possible longest valid concatenations are "chaers" ("cha" + "ers") and "acters" ("act" + "ers").</code></pre>

{% hint style="info" %}
确定index 位置 str是否在字符串中出现过 然后加上后面是否出现过

time  **O(2^n)**  space  **O(n)**
{% endhint %}

```
class Solution {
    public int maxLength(List<String> arr) {
        return helper(arr, 0, "");
    }
    
    private int helper(List<String> arr, int index, String cur) {
        if (index == arr.size()) return cur.length();
        
        int res = cur.length();
        for (int i = index; i < arr.size(); i++) {
            String str = cur + arr.get(i);
            if (isUnique(str)) {
                res = Math.max(res, helper(arr, i + 1, str));
            }
        }
        return res;
    }
    
    private boolean isUnique(String s) {
        Set<Character> set = new HashSet();
        for (char c : s.toCharArray()) {
            if (!set.add(c)) return false;
        }
        return true;
    }
}
```
