# Animal Shelter

> An animal shelter holds only `dogs` and `cats`, and operates on a strictly `"first in, first out"` basis. People must adopt either the `"oldest"` (based on arrival time) of all animals at the shelter, or they can select whether they would prefer a dog or a cat (and will receive the oldest animal of that type). They cannot select which specific animal they would like. Create the data structures to maintain this system and implement operations such as `enqueue`, `dequeueAny`, `dequeueDog` and `dequeueCat`.\
>
>
> Example
>
> **Example 1**
>
> ```
> Input:
> enqueue("james", 1)
> enqueue("tom", 1)
> enqueue("mimi", 0)
> dequeueAny()
> dequeueCat()
> dequeueDog()
>
> Output:
> ["james","mini","tom"]
> ```
>
> **Example 2**
>
> ```
> Input:
> enqueue("a",1)
> enqueue("Tom",0)
> dequeueAny()
> dequeueAny()
>
> Output:
> ["a","Tom"]
> ```

```
class Node {
    int time;
    String name;

    Node(String name, int time) {
        this.name = name;
        this.time = time;
    }
    public String getName() {
        return this.name;
    }
    public int getTime() {
        return this.time;
    }
}

public class AnimalShelter {

    private int tot;
    private LinkedList<Node> cats, dogs;

    public AnimalShelter() {
        // do initialize if necessary
        tot = 0;
        dogs = new LinkedList<Node>();
        cats = new LinkedList<Node>();
    }

    public void enqueue(String name, int type) {
        tot += 1;
        if (type == 1) {
            dogs.add(new Node(name, tot));
        } else {
            cats.add(new Node(name, tot));
        }
    }

    public String dequeueAny() {
        if (cats.isEmpty()) {
            return dequeueDog();
        } else if (dogs.isEmpty()) {
            return dequeueCat();
        } else {
            int dogTime = dogs.getFirst().getTime();
            int catTime = cats.getFirst().getTime();
            if (catTime < dogTime) {
                return dequeueCat();
            } else {
                return dequeueDog();
            }
        }
    }
    
    public String dequeueDog() {
        String name = dogs.getFirst().getName();
        dogs.removeFirst();
        return name;
    }

    public String dequeueCat() {
        String name = cats.getFirst().getName();
        cats.removeFirst();
        return name;
    }
}
```
