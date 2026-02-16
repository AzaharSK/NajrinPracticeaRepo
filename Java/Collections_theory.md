----------------------------------------------------------------------------------------------------
# INDEX based Random access with Duplicate elements are allowed.

## Fixed Size Array
- Continuous memory block

```java
int[] arr = new int[5];
arr[0] = 10;
arr[1] = 20;
```
- Provide Faster index based random access.
- Maintains insertion order
- Size cannot change after creation.
- You can not inser 6th element in this aaray, It will throw excaption "Out-of-bound"
- Array is not thread safe.


## Dynamic Array:

<img width="500" height="217" alt="image" src="https://github.com/user-attachments/assets/3833efcf-a83c-478f-ada7-7903a87b60e2" />
<img width="1280" height="1510" alt="image" src="https://github.com/user-attachments/assets/fdfcacc3-18d3-478d-ac6f-9ae730f41a36" />

## ArrayList:

ArrayList in Java is a `dynamically resizable` array provided in the `java.util package`. Unlike fixed sized arrays, ArrayList's size `can grow (1.5x grow) or shrink dynamically` as elements are added or removed.

- ArrayList default capacity becomes 10 x size_of_element - on first insertion , and grows by 50% (1.5x) when full.
- Elements can be accessed using their index, just like arrays.
- Duplicate elements are allowed.
- Maintains insertion order
- Elements are stored in the order they are inserted.
- ArrayList is not thread-safe. To make it thread-safe, you must wrap it manually using Collections.synchronizedList().
- Proved Balanced memory usages + performance

```java
import java.util.ArrayList;

ArrayList<Integer> list = new ArrayList<>();
list.add(10);
list.add(20);
list.remove(0);

```
- Resizable automatically.

## Vector :
Vector is a legacy dynamic array in java.util that is synchronized (thread-safe) by default.

<img width="523" height="292" alt="image" src="https://github.com/user-attachments/assets/8c21bb32-9aeb-485b-a406-11c59f80cad3" />



```java
import java.util.Vector;

Vector<Integer> v = new Vector<>();
v.add(10);
v.add(20);
v.add(30);
```
- Default capacity = 10
- Performance: Slower than ArrayList, and wastes memory.
- Multithreaded legacy system.

<img width="1782" height="833" alt="image" src="https://github.com/user-attachments/assets/19bc1e9f-8899-4df4-8cff-4e63436604be" />
<img width="1784" height="8039" alt="image" src="https://github.com/user-attachments/assets/02e5d819-10b8-44a3-b799-a325a1ba44e4" />



### Array is fixed size and fastest but cannot grow.
### ArrayList is dynamic, non-synchronized, and most commonly used.
### Vector is dynamic but synchronized, making it thread-safe but slower, and mostly legacy.

--------------------------------------------


# Linked List:

Like arrays, Linked List is a linear data structure.But linked list elements are not stored at the contiguous location, the elements are linked using pointers as shown below. 


<img width="899" height="188" alt="image" src="https://github.com/user-attachments/assets/c5a57fb9-3b0b-4392-85a3-291a8b2d7797" />
<img width="679" height="251" alt="image" src="https://github.com/user-attachments/assets/7b60fa1b-aa64-474e-825e-33ae3a81c0c6" />

-  Linked List not continuous memory, elements/nodes are scattered in memory, Direct index access not possible , but itterative traversal or access is sequential.

```
 for(Integer n : list)
    System.out.println(n);
```

- `Key Strength of LinkedList:` Adding Element to list shifting is not required as It is required in Array/ArrayList/Vector, we can directly add node at the begining and update head refernce.  

<img width="745" height="333" alt="image" src="https://github.com/user-attachments/assets/7e9c4537-a162-4295-b1b1-5b83729dbd4b" />

- `Doubly linked List:` can travarse both direction ( Left -> right) or (right->left)

<img width="801" height="401" alt="image" src="https://github.com/user-attachments/assets/cc46dc06-cb5e-4239-9a4e-8b6b408de7fe" />


```java
    /* Linked list Node*/
    static class Node {
        int data;
        Node next;

        // Constructor to create a new node
        // Next is by default initialized
        // as null
        Node(int d) { data = d; }
    }
```

```java
class LinkedList {
    Node head; // head of list
    
}
```

- A linked list is a collection of nodes where each node contains data and a reference to the next node. The head pointer stores the first node. Traversal is sequential (O(n)),
- but insertion and deletion are efficient because only pointer manipulation is required.

## Types of LinkedList:
Singly Linked List - Has single - `next` reference link
Doubly Linked List - Has double - `next` and `prev` reference links
Circular Linked List - is a linked list where the last node does NOT point to null - Used in Circular Queue / Ring Buffer concept - where data Overwriten after reaching max capacity.

## LinkedList collection in Java offering fast insertion and deletion but slow random access.
LinkedList implements 

```
List interface
Deque interface
```
- It is based on a doubly linked list data structure.
- That means each node contains:
- `| previous ← data → next |`


```java
import java.util.LinkedList;

public class Demo {
    public static void main(String[] args) {

        LinkedList<String> list = new LinkedList<>();

        // Add elements
        list.add("Apple");
        list.add("Banana");
        list.addFirst("Mango");
        list.addLast("Orange");

        System.out.println(list);

        // Access
        System.out.println(list.get(1));

        // Remove
        list.removeFirst();
        list.removeLast();

        System.out.println(list);
    }
}
```

` Usage:`
- LinkedList is bad for random access - so where random index based access required - LinkedList is not used
- LinkedList is Good for frequent insert/delete operations - LinkedList is used where frequent user data insert/delete operations required on-demand basis.
