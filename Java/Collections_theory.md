----------------------------------------------------------------------------------------------------
# INDEX based Random access with Duplicate elements are allowed.


<img width="500" height="217" alt="image" src="https://github.com/user-attachments/assets/3833efcf-a83c-478f-ada7-7903a87b60e2" />

<img width="1280" height="1510" alt="image" src="https://github.com/user-attachments/assets/fdfcacc3-18d3-478d-ac6f-9ae730f41a36" />


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
  
## ArrayList in Java

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

## Vector 
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
<img width="1084" height="809" alt="image" src="https://github.com/user-attachments/assets/02e5d819-10b8-44a3-b799-a325a1ba44e4" />



### Array is fixed size and fastest but cannot grow.
### ArrayList is dynamic, non-synchronized, and most commonly used.
### Vector is dynamic but synchronized, making it thread-safe but slower, and mostly legacy.

--------------------------------------------
