# Open the Lock

[https://leetcode.com/problems/open-the-lock/](https://leetcode.com/problems/open-the-lock/)

```
class Solution {
    public int openLock(String[] deadends, String target) {
        String start = "0000";
        Set<String> deadSet = new HashSet<>();
        for (String str : deadends) {
            if (str.equals(start)) return -1;
            deadSet.add(str);
        }
        int res = 0;
        Set<String> set = new HashSet<>();
        Queue<String> q = new LinkedList<>();
        q.offer(start);
        set.add(start);
        while (!q.isEmpty()) {
            int size = q.size();
            for (int i = 0; i < size; i++) {
                String cur = q.poll();
                if (cur.equals(target)) return res;
                for (int j = 0; j < 4; j++) {
                    String next = cur.substring(0, j) + (char)((cur.charAt(j) - '0' + 9) % 10 + '0') + cur.substring(j + 1);
                    if (!set.contains(next) && !deadSet.contains(next)) {
                        set.add(next);
                        q.offer(next);
                    }
                    next = cur.substring(0, j) + (char)((cur.charAt(j) - '0' + 1) % 10 + '0') + cur.substring(j + 1);
                    if (!set.contains(next) && !deadSet.contains(next)) {
                        set.add(next);
                        q.offer(next);
                    }
                }
            }
            res++;
        }
        return -1;
    }
}
```
