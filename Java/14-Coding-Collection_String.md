## convert User Input Strings into ArrayList:
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
