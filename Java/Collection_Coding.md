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
- `Strings`: "Apple" , "Bananan", "Mango", "Apple"   ==Convert==>   ArrayList: ["Apple", "Bananan", "Mango", "Apple"]

- `UserInput.java`
```java
import java.util.*;

public class UserInput {

    // Method to take user input and return ArrayList<Integer>
    public static ArrayList<Integer> getNumbersFromUser() {

        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter numbers separated by comma:");
        String input = scanner.nextLine();

        String[] items = input.split(",");

        ArrayList<Integer> numbers = new ArrayList<>();

        for (String item : items) {
            numbers.add(Integer.parseInt(item.trim()));
        }

        System.out.println("ArrayList: " + numbers);
        return numbers;
    }

    // Method to take user input and return ArrayList<String>
    public static ArrayList<String> getWordsFromUser() {

        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter words separated by comma:");
        String input = scanner.nextLine();

        String[] items = input.split(",");

        ArrayList<String> words = new ArrayList<>();

        for (String item : items) {
            words.add(item.trim());
        }

        System.out.println("ArrayList: " + words);
        return words;
    }
}

```
- `Test.java`
```java
import java.util.*;

public class Test {

    public static void main(String[] args) {

        ArrayList<String> wordsList = UserInput.getWordsFromUser();
        System.out.println("Final Words List: " + wordsList);

        ArrayList<Integer> numbersList = UserInput.getNumbersFromUser();
        System.out.println("Final Numbers List: " + numbersList);
    }
}

```

## Comvert UserInput ino List:
- `Inegers`: 5 , 3, 7, 1, 9 ==Convert==> List: [ 5 , 3, 7, 1, 9]
- `Strings`: "Apple" , "Bananan", "Mango", "Apple" ==Convert==> List: ["Apple", "Bananan", "Mango", "Apple"]

`UserInput.java`
```java
import java.util.*;

public class UserInput {

    // Method to take user input and return List<Integer>
    public static List<Integer> getNumbersFromUser() {

        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter numbers separated by comma:");
        String input = scanner.nextLine();

        String[] items = input.split(",");

        List<Integer> numbers = new ArrayList<>();

        for (String item : items) {
            numbers.add(Integer.parseInt(item.trim()));
        }

        System.out.println("List: " + numbers);
        return numbers;
    }

    // Method to take user input and return List<String>
    public static List<String> getWordsFromUser() {

        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter words separated by comma:");
        String input = scanner.nextLine();

        String[] items = input.split(",");

        List<String> words = new ArrayList<>();

        for (String item : items) {
            words.add(item.trim());
        }

        System.out.println("List: " + words);
        return words;
    }
}

```
`Test.java`
```java
import java.util.*;

public class Test {

    public static void main(String[] args) {

        List<String> wordsList = UserInput.getWordsFromUser();
        System.out.println("Final Words List: " + wordsList);

        List<Integer> numbersList = UserInput.getNumbersFromUser();
        System.out.println("Final Numbers List: " + numbersList);
    }
}
```


---------------------------------------------------
## Remove duplicate elements from `List` or `ArrayList`

- `List`
```java
List<Integer> numbersList = UserInput.getNumbersFromUser();
List<Integer> numbersList = Arrays.asList(1, 2, 3, 2, 4, 1, 5);

// HashSet does NOT allow duplicate elements, converting time, it Remove all duplicates And insertion Order is preserved 
Set<Integer> uniqueSet = new LinkedHashSet<>(numbersList); // [5, 3, 7, 1, 9]

// HashSet does NOT allow duplicate elements, converting time, it Remove all duplicates But Order is NOT preserved 
Set<Integer> uniqueSet = new HashSet<>(numbersList);  // [1, 3, 5, 7, 9]

System.out.println("Unique elements: " + uniqueSet);
```
`ArrayList`
```java
ArrayList<Integer> numbersList = UserInput.getNumbersFromUser();
ArrayList<Integer> numbersList = new ArrayList<>(Arrays.asList(5, 3, 7, 1, 9, 3, 5, 7));

// HashSet does NOT allow duplicate elements, converting time, it Remove all duplicates And insertion Order is preserved 
Set<Integer> uniqueSet = new LinkedHashSet<>(numbersList); // [5, 3, 7, 1, 9]

// HashSet does NOT allow duplicate elements, converting time, it Remove all duplicates But Order is NOT preserved 
Set<Integer> uniqueSet = new HashSet<>(numbersList);  // [1, 3, 5, 7, 9]

System.out.println("Unique elements: " + uniqueSet);
```

----------------------------------

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

---------


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
---




