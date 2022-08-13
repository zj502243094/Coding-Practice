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

### stacks arrays implementation

<pre><code>class ArrayStack {
     private Object[] array;
     private int count;
     public static final int MAX = 100; 

     public ArrayStack() {
          array = new Object[MAX];
          count = 0;
     }

<strong>     public Object top() {
</strong><strong>           return array[count-1];
</strong>     }

      public void pop() {
           count--;
      }

      public void push(Object obj) {
           array[count++]=obj;
      }

      public boolean isEmpty() {
           return count==0;
      }
}</code></pre>

### stacks ArrayList implementation&#x20;

```
class MyStack {
    private List<Integer> data;               // store elements
    public MyStack() {
        data = new ArrayList<>();
    }
    
    /** Insert an element into the stack. */
    public void push(int x) {
        data.add(x);
    }
    
    /** Checks whether the queue is empty or not. */
    public boolean isEmpty() {
        return data.isEmpty();
    }
    
    /** Get the top item from the queue. */
    public int top() {
        return data.get(data.size() - 1);
    }
    
    /** Delete an element from the queue. Return true if the operation is successful. */
    public boolean pop() {
        if (isEmpty()) {
            return false;
        }
        data.remove(data.size() - 1);
        return true;
    }
};
```
