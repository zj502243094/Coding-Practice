# Repeated DNA Sequences

[https://leetcode.com/problems/repeated-dna-sequences/](https://leetcode.com/problems/repeated-dna-sequences/)

> The **DNA sequence** is composed of a series of nucleotides abbreviated as `'A'`, `'C'`, `'G'`, and `'T'`.
>
> * For example, `"ACGAATTCCG"` is a **DNA sequence**.
>
> When studying **DNA**, it is useful to identify repeated sequences within the DNA.
>
> Given a string `s` that represents a **DNA sequence**, return all the **`10`-letter-long** sequences (substrings) that occur more than once in a DNA molecule. You may return the answer in **any order**.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: s = "AAAAACCCCCAAAAACCCCCCAAAAAGGGTTT"
> <strong>Output: ["AAAAACCCCC","CCCCCAAAAA"]</strong></code></pre>
>
> **Example 2:**
>
> <pre><code>Input: s = "AAAAAAAAAAAAA"
> <strong>Output: ["AAAAAAAAAA"]</strong></code></pre>

```
class Solution {
    public List<String> findRepeatedDnaSequences(String s) {
        HashSet<String> s1 = new HashSet<>();
        HashSet<String> s2 = new HashSet<>();
        for (int i = 0; i < s.length() - 9; i++) {
            String tmp = s.substring(i, i + 10);
            if (s1.contains(tmp)) {
                s2.add(tmp);
            }
            s1.add(tmp);
        }
        return new ArrayList<>(s2);
    }
}
```
