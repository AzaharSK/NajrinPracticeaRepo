## Which Collection When ?
```sql
- ✅ 1️⃣ Fast Searching :                     HashSet/HashMap     set.contains(5);  // Very fast  O(1)
- ✅ 2️⃣ Fast Random Access (get by index):   ArrayList           numbers.get(3);  // Very fast O(1)
- ✅ 3️⃣ Fast Insert / Remove in Middle :     LinkedList          list.add("A") / list.add(2, "B");  // Practical performance not always better than ArrayList.  O(n)
- ✅ 4️⃣ Remove by Value Fastest:             HashSet/HashMap     set.remove("Banana"); // Very fast ,Because lookup is O(1).
- ✅ 5️⃣ Automatic Sorting Needed:            TreeSet/TreeMap     tree.add(5)  // maintain sorted order automatically during insertion. O(log n)
- ✅ 5️⃣ QUeue FIFO (First In → First Out) :  ArrayDeque          queue.offer(10) & queue.poll() // offer() / poll() /peek() → Very fast O(1) 
```

## convert User Input into ArrayList:
- `Inegers`: 5 , 3, 7, 1, 9   ==Convert==>   ArrayList: [ 5 , 3, 7, 1, 9]

```java
import java.util.*;

public class Test {

    public static void main(String[] args) {
        
        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter numbers separated by comma:");
        String input = scanner.nextLine();

        String[] items = input.split(",");

        List<Integer> numbers = new ArrayList<>();

        for (String item : items) {
            numbers.add(Integer.parseInt(item.trim()));
        }

        System.out.println("Final Numbers List: " + numbers);
    }
}
```
## convert User Input into ArrayList:
- `Strings`: "Apple" , "Bananan", "Mango", "Apple"   ==Convert==>   ArrayList: ["Apple", "Bananan", "Mango", "Apple"]

```java
import java.util.*;

public class Test {

    public static void main(String[] args) {
        
        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter words separated by comma:");
        String input = scanner.nextLine();

        String[] items = input.split(",");

        ArrayList<String> words = new ArrayList<>();

        for (String item : items) {
            words.add(item.trim());
        }

        System.out.println("ArrayList: " + words);
    }
}

```
---------------------------------------------------
## Iterate a list<int> one by one element

```java
List<Integer> numbers = new ArrayList<>(Arrays.asList(5, 3, 7, 1, 9));
for (Integer num : numbers) {
    System.out.println(num);
}
```
```java
// even shorter way:
numbers.forEach(System.out::println);
```

```java
// OLD style
for (int i = 0; i < numbers.size(); i++) {
    System.out.println(numbers.get(i));
}
```

------------------------------------------------------------
## Check Empty collection or not ?
- Almost all collections and map interface  has `isEmpty()` to check collection empty or not ? It return `True` or `False`
- supported in all these class `ArrayList, List, LinkedList, Vector, HashSet, TreeSet, Queue, ArrayDeque, LinkedList, PriorityQueue, HashMap, TreeMap, Hashtable, Stack class`
```java
List<Integer> list = new ArrayList<>();
if (list.isEmpty()) {
    System.out.println("List is empty");
}
```
```java
Set<String> set = new HashSet<>();
if (set.isEmpty()) {
    System.out.println("Set is empty");
}
```
```java
Map<String, Integer> map = new HashMap<>();
if (map.isEmpty()) {
    System.out.println("Map is empty");
}
```
```java
Queue<Integer> queue = new ArrayDeque<>();
if (queue.isEmpty()) {
    System.out.println("Queue is empty");
}
```

------------------------------
## FindElement present or not ?
```java
List<Integer> numbers = new ArrayList<>(Arrays.asList(5, 3, 7, 1, 9));
boolean found = numbers.contains(key);   // key = 7 check if number exists  , return True or False
```
---------------------------------
## Count ElementOccurenceFrequency in array java collection 
```java
List<Integer> numbers = Arrays.asList(5, 3, 7, 1, 9, 3, 5, 3);
int freqCount = Collections.frequency(numbers, key); // key =3

// System.out.println("3 occurs " + freqCount + " times");
```

----------

## Find Max Repeating Element in a List of numbers

```java
public static int findMaxRepeatingElement(List<Integer> numbers) {
        int maxCount = 0;
        int maxRepeatingElement = numbers.get(0);

        for (int key : numbers) {
            int count = Collections.frequency(numbers, key);
            if (count > maxCount) {
                maxCount = count;
                maxRepeatingElement = key;
            }
        }

        return maxRepeatingElement;
    }

List<Integer> numbers = Arrays.asList(5, 3, 7, 3, 1, 3, 5, 9);
int result = findMaxRepeatingElement(numbers);

// System.out.println("Max repeating element: " + result);
```
----
## Find if array/list Has any Duplicates.

```java
// Method to check if a list has duplicates
public static boolean hasDuplicates(List<Integer> numbers) {

    // HashSet stores only unique elements
    Set<Integer> unique = new HashSet<>(numbers);

    // If size is same, no duplicates
    if (unique.size() == numbers.size())
        return false;
     else
        return true;
}

List<Integer> numbers = Arrays.asList(5, 3, 7, 1, 9, 3);
boolean hasDulicateX = hasDuplicates(numbers);
```

-----------------------------------------------------------------
## Find Duplicates in array

```java
 public static Set<Integer> findDuplicates(List<Integer> numbers) {
        Set<Integer> seen = new HashSet<>();
        Set<Integer> duplicates = new HashSet<>();

        for (int num : numbers) {
            if (!seen.add(num)) { // add() returns false if element already exists
                duplicates.add(num);
            }
        }

        return duplicates;
    }

List<Integer> numbers = Arrays.asList(5, 3, 7, 3, 1, 3, 5, 9);
Set<Integer> duplicates = findDuplicates(numbers);
// System.out.println("Duplicates in array: " + duplicates);
```
---------------------------------------------------------------
## Remove duplicate elements from `List` or `ArrayList`

- `List`
```java
List<Integer> numbersList = UserInput.getNumbersFromUser();
List<Integer> numbersList = Arrays.asList(1, 2, 3, 2, 4, 1, 5);

// HashSet does NOT allow duplicate elements, converting time, it Remove all duplicates And insertion Order is preserved 
Set<Integer> uniqueSet = new LinkedHashSet<>(numbersList); //  // [1, 3, 5, 7, 9] 

// HashSet does NOT allow duplicate elements, converting time, it Remove all duplicates But Order is NOT preserved 
Set<Integer> uniqueSet = new HashSet<>(numbersList);  //[5, 3, 7, 1, 9]

System.out.println("Unique elements: " + uniqueSet);
```
`ArrayList`
```java
ArrayList<Integer> numbersList = UserInput.getNumbersFromUser();
ArrayList<Integer> numbersList = new ArrayList<>(Arrays.asList(5, 3, 7, 1, 9, 3, 5, 7));

// HashSet does NOT allow duplicate elements, converting time, it Remove all duplicates And insertion Order is preserved 
Set<Integer> uniqueSet = new LinkedHashSet<>(numbersList); //  [1, 3, 5, 7, 9] 

// HashSet does NOT allow duplicate elements, converting time, it Remove all duplicates But Order is NOT preserved 
Set<Integer> uniqueSet = new HashSet<>(numbersList);  //[5, 3, 7, 1, 9]

System.out.println("Unique elements: " + uniqueSet);
```

----------------------------------

## check if Array (Unsorted) is Subset of another array (Unsorted) 

```java
public static boolean isSubset(List<Integer> subset, List<Integer> superset) {
        // Create a HashSet from superset for fast lookup
        Set<Integer> supersetSet = new HashSet<>(superset);

        // Check if each element of subset exists in superset
        for (int elem : subset) {
            if (!supersetSet.contains(elem)) {
                return false;
            }
        }
        return true;
    }

List<Integer> subset = Arrays.asList(3, 7, 1);
List<Integer> superset = Arrays.asList(5, 3, 7, 1, 9);

if (isSubset(subset, superset)) {  // True
} else { // Flase  }
```

---------------------------------

## Find below for List Numbers
- `Inegers`: 5 , 3, 7, 1, 9   ==Convert==>   ArrayList: [ 5 , 3, 7, 1, 9]
- ✅ Sum
- ✅ Average
- ✅ Maximum
- ✅ Minimum

```java
import java.util.*;

public class Test {

    public static void main(String[] args) {
        
        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter numbers separated by comma:");
        String input = scanner.nextLine();

        String[] items = input.split(",");

        List<Integer> numbers = new ArrayList<>();

        for (String item : items) {
            numbers.add(Integer.parseInt(item.trim()));
        }

        System.out.println("Final Numbers List: " + numbers);

        if (numbers.isEmpty()) {
            System.out.println("List is empty.");
            return;
        }

        // ✅ Sum
        int sum = 0;
        for (int num : numbers) {
            sum += num;
        }

        // ✅ Average
        double average = (double) (sum / numbers.size());

        // ✅ Max and Min
        int max = Collections.max(numbers);
        int min = Collections.min(numbers);

        // Output
        System.out.println("Sum: " + sum);
        System.out.println("Average: " + average);
        System.out.println("Maximum: " + max);
        System.out.println("Minimum: " + min);
    }
}
```

## Sorting  Application:
### numbers sorting
```java
import java.util.*;

public class Test {
    public static void main(String[] args) {

        List<Integer> numbers = new ArrayList<>(Arrays.asList(5, 3, 7, 1, 9));

        Collections.sort(numbers);  // Ascending order
        System.out.println("Sorted List (Ascending): " + numbers);  // Modifies original list 'numbers' // OutPut: Sorted List (Ascending): [1, 3, 5, 7, 9]

        Collections.sort(numbers, Collections.reverseOrder());
        System.out.println("Sorted List (Descending): " + numbers);   //  Modifies original list 'numbers' //  Sorted List (Descending): [9, 7, 5, 3, 1]
    }
}
```
### String sorting
```java
import java.util.*;

public class Test {

    public static void main(String[] args) {

        List<String> names = new ArrayList<>(
                Arrays.asList("Banana", "Apple", "Mango", "Cherry"));

        System.out.println("Original: " + names);
        // Original: [Banana, Apple, Mango, Cherry]

        // 1️⃣ Ascending (Default - Lexicographical Order)
        Collections.sort(names);
        System.out.println("Ascending: " + names);
        // Ascending: [Apple, Banana, Cherry, Mango]

        // 2️⃣ Descending
        Collections.sort(names, Collections.reverseOrder());
        System.out.println("Descending: " + names);
        // Descending: [Mango, Cherry, Banana, Apple]

        // 3️⃣ Case-Insensitive Sorting
        List<String> names2 = new ArrayList<>(
                Arrays.asList("banana", "Apple", "mango", "Cherry"));

        names2.sort(String.CASE_INSENSITIVE_ORDER);
        System.out.println("Case-Insensitive Sort: " + names2);
        // Case-Insensitive Sort: [Apple, banana, Cherry, mango]

        // 4️⃣ Sort by Length
        names2.sort(Comparator.comparingInt(String::length));
        System.out.println("Sorted by Length: " + names2);
        // Sorted by Length: [Apple, mango, banana, Cherry]
    }
}
````
