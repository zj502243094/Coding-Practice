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
	
	static int mostFrequent(int arr[], int n){
		
		Map<Integer, Integer> hp = new HashMap<Integer, Integer>();
		
		for(int i = 0; i < n; i++) {
			int key = arr[i];

		}
		
		// find max frequency.
		int max_count = 0, res = -1;
		
		for(Entry<Integer, Integer> val : hp.entrySet())
		{
			if (max_count < val.getValue())
			{
				res = val.getKey();
				max_count = val.getValue();
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

// This code is contributed by Akash Singh.

```
