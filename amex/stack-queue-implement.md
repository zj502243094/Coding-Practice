# Stack / Queue implement

### Queue Using Array

Use a **fixed-size array** and **two pointers** to indicate the starting position and the ending position. And the goal is to **reuse** the **wasted** **storage** we mentioned previously.

```
class ArrayQueue {
    private int front,back;
    private Object[] array;
    public static final int MAX=100;

    public ArrayQueue() {
        front=0;
        back=0;
        array = new Object[MAX];
    }

    public Object first() {
        return array[front];
    }

    public void leave(){
        front++;
        if(front==MAX)
        front=0;
    }

    public void join(Object obj) {
        array[back++]=obj;
        if(back==MAX)
            back=0;
    }

    public boolean isEmpty() {
        return front==back;
    }
}
```

### Stacks arrays implementation

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

### Stacks ArrayList implementation&#x20;

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
