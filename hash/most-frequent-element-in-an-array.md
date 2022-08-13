# Most frequent element in an array

[https://www.geeksforgeeks.org/frequent-element-array/](https://www.geeksforgeeks.org/frequent-element-array/)

> Given an array, find the most frequent element in it. If there are multiple elements that appear a maximum number of times, print any one of them.
>
> **Examples:**&#x20;
>
> > **Input :** arr\[] = {1, 3, 2, 1, 4, 1}\
> > **Output :** 1\
> > **Explanation:** 1 appears three times in array which is maximum frequency.
> >
> > **Input :** arr\[] = {10, 20, 10, 20, 30, 20, 20}\
> > **Output :** 20

```
class GFG {
	
	static int mostFrequent(int arr[]){
		
		Map<Integer, Integer> map = new HashMap<Integer, Integer>();
		
		for (int num : arr[]){
			map.put(nums, map.getOrDefault(nums, 0) + 1);
		}
		
		// find max frequency.
		int max = 0, res = 0;
		
		for(Entry<Integer, Integer> val : map.entrySet()){
			if (max < val.getValue()){
				res = val.getKey();
				max = val.getValue();
			}
		}
		return res;
	}
	
	// Driver code
	public static void main (String[] args) {
		
		int arr[] = {40,50,30,40,50,30,30};
		int n = arr.length;
		
		System.out.println(mostFrequent(arr, n));
	}
}

```

```
static int maxFreq(int[] arr){
   
    int res = 0;
    int count = 1;
    for(int i = 1; i < arr.length; i++) {
        if(arr[i] == arr[res]) {
            count++;
        } else {
            count--;
        }
 
        if(count == 0) {
            res = i;
            count = 1;
        } 
    } 
    return arr[res];
}
```
