# Word Ladder II

[https://leetcode.com/problems/word-ladder-ii/](https://leetcode.com/problems/word-ladder-ii/)

> A **transformation sequence** from word `beginWord` to word `endWord` using a dictionary `wordList` is a sequence of words `beginWord -> s1 -> s2 -> ... -> sk` such that:
>
> * Every adjacent pair of words differs by a single letter.
> * Every `si` for `1 <= i <= k` is in `wordList`. Note that `beginWord` does not need to be in `wordList`.
> * `sk == endWord`
>
> Given two words, `beginWord` and `endWord`, and a dictionary `wordList`, return _all the **shortest transformation sequences** from_ `beginWord` _to_ `endWord`_, or an empty list if no such sequence exists. Each sequence should be returned as a list of the words_ `[beginWord, s1, s2, ..., sk]`.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: beginWord = "hit", endWord = "cog", wordList = ["hot","dot","dog","lot","log","cog"]
> <strong>Output:
> </strong> [["hit","hot","dot","dog","cog"],["hit","hot","lot","log","cog"]]
> <strong>Explanation:
> </strong> There are 2 shortest transformation sequences:
> "hit" -> "hot" -> "dot" -> "dog" -> "cog"
> "hit" -> "hot" -> "lot" -> "log" -> "cog"</code></pre>

{% hint style="info" %}
单向BFS 找到路径 再DFS打印所有路径
{% endhint %}

```
class Solution {
    public List<List<String>> findLadders(String beginWord, String endWord, List<String> wordList) {
        Set<String> dict = new HashSet<>(wordList);
        List<List<String>> res = new ArrayList<>();
        if (!dict.contains(endWord)) return res;
        Map<String, List<String>> nodeNeighbors = new HashMap<>();
        Map<String, Integer> distance = new HashMap<>();
        List<String> paths = new ArrayList<>();
        dict.add(beginWord);
        bfs(beginWord, endWord, dict, nodeNeighbors, distance);
        dfs(beginWord, endWord, dict, nodeNeighbors, distance, paths, res);
        return res;
    }
    private void bfs(String beginWord, String endWord, Set<String> dict, 
                     Map<String, List<String>> nodeNeighbors, Map<String, Integer> distance) {
        for (String str : dict) {
            nodeNeighbors.put(str, new ArrayList<>());
        }
        Queue<String> q = new LinkedList<>();
        q.offer(beginWord);
        distance.put(beginWord, 0);
        while (!q.isEmpty()) {
            int size = q.size();
            boolean found = false;
            for (int i = 0; i < size; i++) {
                String cur = q.poll();
                int curDis = distance.get(cur);
                List<String> neighbors = getNeighbor(cur, dict);
                for (String neighbor : neighbors) {
                    nodeNeighbors.get(cur).add(neighbor);
                    if (!distance.containsKey(neighbor)) {
                        distance.put(neighbor, curDis + 1);
                        if (neighbor.equals(endWord)) found = true;
                        else q.offer(neighbor);
                    }
                }
            }
            if (found) break;
        }
    }
    private List<String> getNeighbor(String cur, Set<String> dict) {
        List<String> res = new ArrayList<>();
        char[] chs = cur.toCharArray();
        for (int i = 0; i < chs.length; i++) {
            for (char c = 'a'; c <= 'z'; c++) {
                char pre = chs[i];
                if (pre == c) continue;
                chs[i] = c;
                if (dict.contains(String.valueOf(chs))) {
                    res.add(String.valueOf(chs));
                }
                chs[i] = pre;
            }
        }
        return res;
    }
    private void dfs(String cur, String endWord, Set<String> dict, 
                     Map<String, List<String>> nodeNeighbors, Map<String, Integer> distance, 
                     List<String> paths, List<List<String>> res) {
        paths.add(cur);
        if (endWord.equals(cur)) {
            res.add(new ArrayList<>(paths));
        } else {
            for (String next : nodeNeighbors.get(cur)) {
                if (distance.get(next) == distance.get(cur) + 1) {
                    dfs(next, endWord, dict, nodeNeighbors, distance, paths, res);
                }
            }
        }
        paths.remove(paths.size() - 1);
    }
}
```

```
class Solution {
    public List<List<String>> findLadders(String beginWord, String endWord, List<String> wordList) {
        Set<String> dict = new HashSet(wordList);
        if( !dict.contains(endWord) )
            return new ArrayList();
        
        // adjacent words for each word
        Map<String,List<String>> adjacency = new HashMap();
        Queue<String> queue = new LinkedList();
        // does path exist?
        boolean found = false;
        
        // BFS for shortest path, keep removing visited words
        queue.offer(beginWord);
        dict.remove(beginWord);
                
        while( !found && !queue.isEmpty() ) {
            int size = queue.size();
            // adjacent words in current level
            HashSet<String> explored = new HashSet();

            while( size > 0 ) {
                String word = queue.poll();
                
                if( adjacency.containsKey(word) )
                    continue;
                
                // remove current word from dict, and search for adjacent words
                dict.remove(word);
                List<String> adjacents = getAdjacents(word, dict);
                adjacency.put(word, adjacents);

                for(String adj : adjacents) {
                    if( !found && adj.equals(endWord) ) 
                        found = true;
                    
                    explored.add(adj);
                    queue.offer(adj);
                }
                size--;
            }
            // remove words explored in current level from dict
            for(String word : explored)
                dict.remove(word);
        }

        // if a path exist, dfs to find all the paths
        if( found ) 
            return dfs(beginWord, endWord, adjacency, new HashMap());
        else
            return new ArrayList();
    }
    
    private List<String> getAdjacents(String word, Set<String> dict) {
        List<String> adjs = new ArrayList();
        char[] wordChars = word.toCharArray();
        
        for(int i=0; i<wordChars.length; i++) 
            for(char c='a'; c<='z'; c++) {
                char temp = wordChars[i];
                wordChars[i] = c;
                
                String newAdj = new String(wordChars);
                if( dict.contains(newAdj) )
                    adjs.add(newAdj);
                
                wordChars[i] = temp;
            }
        return adjs;
    }
    
    private List<List<String>> dfs(String src, String dest, 
                                   Map<String,List<String>> adjacency, 
                                   Map<String,List<List<String>>> memo) {
        if( memo.containsKey(src) )
            return memo.get(src);
        
        List<List<String>> paths = new ArrayList();
        
		// reached dest? return list with dest word
        if( src.equals( dest ) ) {
            paths.add( new ArrayList(){{ add(dest); }} );
            return paths;
        }

		// no adjacent for curr word? return empty list
        List<String> adjacents = adjacency.get(src);
        if( adjacents == null || adjacents.isEmpty() )
            return paths;

        for(String adj : adjacents) {
            List<List<String>> adjPaths = dfs(adj, dest, adjacency, memo);
            
            for(List<String> path : adjPaths) {
                if( path.isEmpty() ) continue;
                
                List<String> newPath = new ArrayList(){{ add(src); }};
                newPath.addAll(path);
                
                paths.add(newPath);
            }
        } 
        memo.put(src, paths);
        return paths;
    }
}
```

```
class Solution {
    private Set<String> dict;
    private String beginWord;
    private String endWord;
    
    // Key: String  Value: parents in the sense that close to beginWord/endWord;
    private Map<String, List<String>> forwardMap = new HashMap<>(); 
    private Map<String, List<String>> backwardMap = new HashMap<>(); 
    
    // Key: String (always appears in a path)  Value: list of String that could be the next String in some paths
    private Map<String, List<String>> pathMap = new HashMap<>();
    
    private Set<String> intersect;
    
    private List<List<String>> paths = new ArrayList<>();
    
    public List<List<String>> findLadders(String beginWord, String endWord, List<String> wordList) {
        this.dict = new HashSet(wordList);
        if (!dict.contains(endWord)) return paths;
        
        this.beginWord = beginWord;
        this.endWord = endWord;
        
        this.intersect = buildMaps();
        if (intersect.size() == 0) return paths;
        
        trimForwardMap();
        trimBackwardMap();
        
        List<String> curr = new ArrayList<>();
        curr.add(beginWord);
        collectAllPaths(beginWord, curr);
        
        return paths;
    }
    
    private void collectAllPaths(String s, List<String> curr) {
        if (s.equals(endWord)) {
            paths.add(new ArrayList(curr));
            return;
        }
        
        for (String next : pathMap.get(s)) {
            curr.add(next);
            collectAllPaths(next, curr);
            curr.remove(curr.size() - 1);
        }
        
    }
    
    
    private Set<String> buildMaps() {
        Set<String> forward = new HashSet<>();
        forward.add(beginWord);
        
        Set<String> backward = new HashSet<>();
        backward.add(endWord);
        
        Set<String> visited = new HashSet<>();
        Set<String> intersect = new HashSet<>();
       
        boolean found = false;
        boolean reverse = false;   
        
     
        while(!forward.isEmpty() && !found) {
            if (forward.size() > backward.size()) {
                Set<String> temp = forward;
                forward = backward;
                backward = temp;
                reverse = !reverse;
            }
            
            Set<String> temp = new HashSet<>(); 
            
            for (String s : forward) {
                visited.add(s);
                
                for (String next : getNext(s)) {
                    if (forward.contains(next) || visited.contains(next)) continue;
                    if (backward.contains(next)) {
                        found = true;
                        intersect.add(next);
                    }
                    
                    temp.add(next);
                    
                    if (reverse) {
                        backwardMap.putIfAbsent(next, new ArrayList<>());
                        backwardMap.get(next).add(s);
                    } else {
                        forwardMap.putIfAbsent(next, new ArrayList<>());
                        forwardMap.get(next).add(s);
                    }
                }
            }
            
            forward = temp;
        }
      
        return intersect;
    }
    
    private void trimForwardMap() {
        Deque<String> queue = new LinkedList<>();
        intersect.stream().forEach(s -> queue.offerLast(s));
        
        Set<String> visited = new HashSet(intersect);
        
        while (!queue.isEmpty()) {
            String s = queue.pollFirst();
            if (!forwardMap.containsKey(s)) return;   // reach beginword
            
            for (String p : forwardMap.get(s)) {
                pathMap.putIfAbsent(p, new ArrayList<>());
                pathMap.get(p).add(s);
                
                if (visited.add(p)) queue.offerLast(p);
            }
        }
        return;
    }
    
    private void trimBackwardMap() {
        Deque<String> queue = new LinkedList<>();
        intersect.stream().forEach(s -> queue.offerLast(s));
        
        Set<String> visited = new HashSet(intersect);
        
        while (!queue.isEmpty()) {
            String s = queue.pollFirst();
            if (!backwardMap.containsKey(s)) return;   // reach endWord
            
            for (String d : backwardMap.get(s)) {
                pathMap.putIfAbsent(s, new ArrayList<>());
                pathMap.get(s).add(d);
                
                if (visited.add(d)) queue.offerLast(d);
            }
        }
        return;
    }
    
    private List<String> getNext(String s) {
        char[] arr = s.toCharArray();
        List<String> nbs = new ArrayList<>();
   
        for (int i = 0; i < arr.length; i++) {
            char ch = arr[i];
            for (char c = 'a'; c <= 'z'; c++) {
                if (c == ch) continue;
                arr[i] = c;
                String nb = new String(arr);
                if (dict.contains(nb)) nbs.add(nb);
            }
            arr[i] = ch;
        }
        
        return nbs;
    }
}
```
