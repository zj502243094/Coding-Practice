# Group Anagrams

[https://leetcode.com/problems/group-anagrams/](https://leetcode.com/problems/group-anagrams/)

> Given an array of strings `strs`, group **the anagrams** together. You can return the answer in **any order**.
>
> An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: strs = ["eat","tea","tan","ate","nat","bat"]
> Output: [["bat"],["nat","tan"],["ate","eat","tea"]]
> ```

{% hint style="info" %}
map key 是 英文单词 排序后的字码 value是同一码对应的全部字符
{% endhint %}

```
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        List<List<String>> res = new ArrayList<>();
        Map<String, List<String>> map = new HashMap();
        
        for (String str : strs){
            char[] cs = str.toCharArray();
            Arrays.sort(cs);
            String sortStr = String.valueOf(cs);
            if (!map.containsKey(sortStr)) map.put(sortStr, new ArrayList<>());
            map.get(sortStr).add(str);
        }
        for(List<String> item : map.values()){
            res.add(item);
        }
        return res;
    }
}
```
