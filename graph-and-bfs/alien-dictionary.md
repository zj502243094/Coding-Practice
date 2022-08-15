# Alien Dictionary

[https://leetcode.com/problems/alien-dictionary/](https://leetcode.com/problems/alien-dictionary/)

```
class Solution {
    Map<Character, List<Character>> graph = new HashMap<>();
    Map<Character, Integer> indegree = new HashMap<>();
    boolean inValid = false;
    public String alienOrder(String[] words) {
        initGraph(words);
        if (inValid) return "";
        StringBuilder sb = new StringBuilder();
        Queue<Character> q = new LinkedList<>();
        for (char c : indegree.keySet()) {
            if (indegree.get(c) == 0) q.offer(c);
        }
        while (!q.isEmpty()) {
            char c = q.poll();
            sb.append(c);
            for (char nei : graph.getOrDefault(c, new ArrayList<>())) {
                indegree.put(nei, indegree.get(nei) - 1);
                if (indegree.get(nei) == 0) q.offer(nei);
            }
        }
        return sb.length() < indegree.size() ? "" : sb.toString();
    }
    
    private void initGraph(String[] words) {
        for (String word : words) {
            for (char c : word.toCharArray()) {
                indegree.put(c, 0);
                graph.put(c, new ArrayList<>());
            }
        }
        for (int i = 0; i < words.length - 1; i++) {
            String word1 = words[i], word2 = words[i + 1];
            if (word1.length() > word2.length() && word1.startsWith(word2)) inValid = true;
            for (int j = 0; j < Math.min(word1.length(), word2.length()); j++) {
                if (word1.charAt(j) != word2.charAt(j)) {
                    graph.get(word1.charAt(j)).add(word2.charAt(j));
                    indegree.put(word2.charAt(j), indegree.get(word2.charAt(j)) + 1);
                    break;
                }
            } 
        }
    }
}
```
