# Merge Two Sorted Arrays

> Description
>
> Merge two given sorted ascending integer array _A_ and _B_ into a new sorted integer array.
>
> ***
>
> Example
>
> **Example 1:**
>
> Input:
>
> ```
> A = [1]
> B = [1]
> ```
>
> Output:
>
> ```
> [1,1]
> ```
>
> Explanation:
>
> return array merged.
>
> **Example 2:**
>
> Input:
>
> ```
> A = [1,2,3,4]
> B = [2,4,5,6]
> ```
>
> Output:
>
> ```
> [1,2,2,3,4,4,5,6]
> ```

```
public class Solution {
    /**
     * @param a: sorted integer array A
     * @param b: sorted integer array B
     * @return: A new sorted integer array
     */
    public int[] mergeSortedArray(int[] a, int[] b) {
        if(a == null) return b;
        if(b == null) return a;
        int lenA = a.length;
        int lenB = b.length;

        int[] res = new int[lenA + lenB];
        int i = 0, j = 0, k = 0;
        while(i < lenA && j < lenB){
            if(a[i] <= b[j]){
                res[k++] = a[i++];
            }else{
                res[k++] = b[j++];
            }
        }
        while(i < lenA) res[k++] = a[i++];
        while(j < lenB) res[k++] = b[j++];
        return res;
    } 
}
```
