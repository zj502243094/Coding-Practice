# Minimum shift Operations Make String Equals

> Given two strings, determine if the first string can be transformed into the second string. The only operation allowed is **moving a character from the first string to the front**. If the string can be transformed, find the minimum number of operations required for the transformation.
>
> For example, the minimum number of operations required to convert the string `ADCB` to string `ABCD` is `3`.
>
> ADCB —> CADB (Move ‘C’ to the front)\
> CADB —> BCAD (Move ‘B’ to the front)\
> BCAD —> ABCD (Move ‘A’ to the front)

```
import java.util.*;
public class Solution {
	public static int minShift(String s1, String s2) {
		if (s1.length() != s2.length()) return -1;
        Map<Character, Integer> map = new HashMap<>();
        for (int i = 0; i < s1.length(); i++) {
            map.put(s1.charAt(i), map.getOrDefault(s1.charAt(i), 0) + 1);
            map.put(s2.charAt(i), map.getOrDefault(s2.charAt(i), 0) - 1);
        }
        for (Character c : map.keySet()) {
            if (map.get(c) != 0) return -1;
        }
        int x = s1.length() - 1, y = s2.length() - 1;
        int res = 0;
        while (x >= 0) {
            if (s1.charAt(x) == s2.charAt(y)) {
                x--;
                y--;
            } else {
                res++;
                x--;
            }
        }
        return res;
	}
}Mi
```
