# Unique Word Abbreviation

[https://leetcode.com/problems/unique-word-abbreviation/](https://leetcode.com/problems/unique-word-abbreviation/)

唯一单词缩写 既要满足 字典中单词缩写唯一 并且其他单词与给定单词缩写无相同

> The **abbreviation** of a word is a concatenation of its first letter, the number of characters between the first and last letter, and its last letter. If a word has only two characters, then it is an **abbreviation** of itself.
>
> For example:
>
> * `dog --> d1g` because there is one letter between the first letter `'d'` and the last letter `'g'`.
> * `internationalization --> i18n` because there are 18 letters between the first letter `'i'` and the last letter `'n'`.
> * `it --> it` because any word with only two characters is an **abbreviation** of itself.
>
> Implement the `ValidWordAbbr` class:
>
> * `ValidWordAbbr(String[] dictionary)` Initializes the object with a `dictionary` of words.
> * `boolean isUnique(string word)` Returns `true` if **either** of the following conditions are met (otherwise returns `false`):
>   * There is no word in `dictionary` whose **abbreviation** is equal to `word`'s **abbreviation**.
>   * For any word in `dictionary` whose **abbreviation** is equal to `word`'s **abbreviation**, that word and `word` are **the same**.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input
> ["ValidWordAbbr", "isUnique", "isUnique", "isUnique", "isUnique", "isUnique"]
> [[["deer", "door", "cake", "card"]], ["dear"], ["cart"], ["cane"], ["make"], ["cake"]]
> Output
> [null, false, true, false, true, true]
> ```

```
class ValidWordAbbr {
    
    Map<String, Integer> dict = new HashMap();
    Map<String, Integer> abbr = new HashMap();

    public ValidWordAbbr(String[] dictionary) {
        for (String d : dictionary) {
            dict.put(d, dict.getOrDefault(d, 0) + 1);
            String a = makeAbbr(d);
            abbr.put(a, abbr.getOrDefault(a, 0) + 1);
        }
    }
    
    public boolean isUnique(String word) {
        String a = makeAbbr(word);
        return dict.getOrDefault(word, 0) == abbr.getOrDefault(a, 0);
    }
    
    private String makeAbbr(String s) {
        if (s.length() <= 2) return s;
        return s.substring(0, 1) + (s.length() - 2) + s.substring(s.length() - 1);
    }
}
```
