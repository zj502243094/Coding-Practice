# Jewels and Stones

[https://leetcode.com/problems/jewels-and-stones/](https://leetcode.com/problems/jewels-and-stones/)

```
class Solution {
    public int numJewelsInStones(String jewels, String stones) {
        int res = 0;
        Set set = new HashSet();
        for (char j : jewels.toCharArray()) set.add(j);
        for (char s : stones.toCharArray()) {
            if (set.contains(s)) res++;
        }
        return res;
    }
}
```
