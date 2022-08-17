# Word Ladder

[https://leetcode.com/problems/word-ladder/](https://leetcode.com/problems/word-ladder/)

> Given two words, `beginWord` and `endWord`, and a dictionary `wordList`, return _the **number of words** in the **shortest transformation sequence** from_ `beginWord` _to_ `endWord`_, or_ `0` _if no such sequence exists._
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: beginWord = "hit", endWord = "cog", wordList = ["hot","dot","dog","lot","log","cog"]
> <strong>Output: 5
> </strong><strong>Explanation:
> </strong> One shortest transformation sequence is "hit" -> "hot" -> "dot" -> "dog" -> cog", which is 5 words long.</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: beginWord = "hit", endWord = "cog", wordList = ["hot","dot","dog","lot","log"]
> <strong>Output: 0
> </strong><strong>Explanation:
> </strong> The endWord "cog" is not in wordList, therefore there is no valid transformation sequence.</code></pre>

```
class Solution {
    public int ladderLength(String beginWord, String endWord, List<String> wordList) {
        Set<String> set = new HashSet<>(wordList);
        Queue<String> q = new LinkedList<>();
        q.offer(beginWord);
        int res = 1;
        int len = beginWord.length();
        while (!q.isEmpty()) {
            int size = q.size();
            for (int i = 0; i < size; i++) {
                String cur = q.poll();
                if (cur.equals(endWord)) return res;
                for (int j = 0; j < len; j++) {
                    for (char c = 'a'; c <= 'z'; c++) {
                        StringBuilder next = new StringBuilder(cur);
                        next.setCharAt(j, c);
                        String nextWord = next.toString();
                        if (set.contains(nextWord)) {
                            if (nextWord.equals(endWord)) return res + 1;
                            set.remove(nextWord);
                            q.offer(nextWord);
                        }
                    }
                }
            }
            res++;
        }
        return 0;
    }
}
```
