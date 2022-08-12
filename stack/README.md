# Stack

A Last-in-first-out (LIFO) Data Structure



Java has a class called java.util.Stack:

`pop()`, `push()`

The [peek()](https://www.geeksforgeeks.org/priorityqueue-peek-method-in-java/) method only retrieved the element at the head but the poll() also removes the element along with the retrieval. It returns NULL if the queue is empty.

```java
// "static void main" must be defined in a public class.
public class Main {
    public static void main(String[] args) {
        // 1. Initialize a stack.
        Stack<Integer> s = new Stack<>();
        // 2. Push new element.
        s.push(5);
        s.push(13);
        s.push(8);
        s.push(6);
        // 3. Check if stack is empty.
        if (s.empty() == true) {
            System.out.println("Stack is empty!");
            return;
        }
        // 4. Pop an element.
        s.pop();
        // 5. Get the top element.
        System.out.println("The top element is: " + s.peek());
        // 6. Get the size of the stack.
        System.out.println("The size is: " + s.size());
    }
}
```
