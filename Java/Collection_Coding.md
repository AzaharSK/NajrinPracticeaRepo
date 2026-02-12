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



```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 2, 4, 1, 5);
Set<Integer> uniqueSet = new HashSet<>(numbers);
System.out.println("Unique elements: " + uniqueSet);
```
