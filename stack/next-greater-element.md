# Next Greater Element

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

![](../.gitbook/assets/image.png)

```
import java.util.*; 
public class Main
{
    public static void main(String[] args) {
        int[] nums = {2, 1, 2, 4, 3};
        // res = {4, 2, 4. -1. -1};
        System.out.println(Arrays.toString(nextGreatElement(nums)));
    }
    private static int[] nextGreatElement(int[] nums) {
        int [] res = new int[nums.length];
        Stack<Integer> stack = new Stack<>();
        for (int i = nums.length - 1; i >= 0; i--) {
            while (!stack.isEmpty() && nums[i] >= stack.peek()) stack.pop();
            res[i] = stack.isEmpty() ? -1 : stack.peek();
            stack.push(nums[i]);
        }
        return res;
    }
}
```
