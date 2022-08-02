# Word Abbreviation

[https://leetcode.com/problems/word-abbreviation/](https://leetcode.com/problems/word-abbreviation/)

单词缩写 头尾不变缩写整个单词 直到被缩写的单词无重复

如果缩写后并没有将单词变短 保留原始单词

> Given an array of **distinct** strings `words`, return _the minimal possible **abbreviations** for every word_.
>
> The following are the rules for a string abbreviation:
>
> 1. The **initial** abbreviation for each word is: the first character, then the number of characters in between, followed by the last character.
> 2. If more than one word shares the **same** abbreviation, then perform the following operation:
>    * **Increase** the prefix (characters in the first part) of each of their abbreviations by `1`.
>      * For example, say you start with the words `["abcdef","abndef"]` both initially abbreviated as `"a4f"`. Then, a sequence of operations would be `["a4f","a4f"]` -> `["ab3f","ab3f"]` -> `["abc2f","abn2f"]`.
>    * This operation is repeated until every abbreviation is **unique**.
> 3. At the end, if an abbreviation did not make a word shorter, then keep it as the original word.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: words = ["like","god","internal","me","internet","interval","intension","face","intrusion"]
> Output: ["l2e","god","internal","me","i6t","interval","inte4n","f2e","intr4n"]
> ```
>
> **Example 2:**
>
> ```
> Input: words = ["aa","aaa"]
> Output: ["aa","aaa"]
> ```

{% hint style="info" %}
wordsAbbreviation()\
首先先将words 缩一遍放到map（字符串， 出现次数）里面

然后进行后面缩减操作， 如果ans\[i] 次数 > 1 表明有重复的 需要更新ans\[i] 对words\[i] 再进行pre\[i]++ 轮次的 缩减 直到unique 出现

\
makeAbbr()&#x20;

第一轮（k = 1）<= 3(s.length) 返回原字符串 第二轮<=4 返回原串 所以轮次k>=s.length() - 2 返回原字符串。然后造这个新string 前面（0， p） + 缩的长度（s.len - 1 - p）\[长度-尾巴-p个prefix] + (s.len() - 1)&#x20;
{% endhint %}

```
class Solution {
    public List<String> wordsAbbreviation(List<String> words) {
        if (words == null) return null;
        int len = words.size();
        int[] prefix = new int[len];
        String[] ans = new String[len];
        Map<String, Integer> map = new HashMap<>();
        
        for (int i = 0; i < len; i++) {
            prefix[i] = 1;
            ans[i] = makeAbbr(words.get(i), 1);
            map.put(ans[i], map.getOrDefault(ans[i], 0) + 1);
        }
        while (true) {
            boolean unique = true;
            for (int i = 0; i < len; i++) {
                if (map.get(ans[i]) > 1) {
                    prefix[i]++;
                    ans[i] = makeAbbr(words.get(i), prefix[i]);
                    map.put(ans[i], map.getOrDefault(ans[i], 0) + 1);
                    unique = false;
                }
            }
            if (unique) break;
        }
        return Arrays.asList(ans);
    }
    private String makeAbbr(String s, int p) {
        if (p >= s.length() - 2) return s;
        return s.substring(0, p) + (s.length() - 1 - p) + s.substring(s.length() - 1);
    }
    
}
```
