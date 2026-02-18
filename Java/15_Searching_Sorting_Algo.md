# Linear Search Or Sequential Search :
- Linear Search is a searching algorithm where - We check each element one by one until we find the target value.
- `Linear/Sequential access or travarsal to array` :
  
<img width="1001" height="471" alt="image" src="https://github.com/user-attachments/assets/5c48543f-b4b3-4a0b-9aa9-e6be17b70935" />
<img width="800" height="427" alt="image" src="https://github.com/user-attachments/assets/66e0fcd7-01d4-4c27-9a90-4d20669a4daa" />

## How It Works:
- Input Array: [10, 20, 30, 40, 50]
- Search Key = 40

```
Step 1 → compare 40 == 10 ? ❌
Step 2 → compare 40 == 20 ? ❌
Step 3 → compare 40 == 30 ? ❌
Step 4 → compare 40 == 40  ? ✔ (found) → @ index 3

It checks elements sequentially.
```

```java
public class Test {

    public static void main(String[] args) {

        int[] arr = {10, 20, 30, 40, 50};

        int key = 40;     // element to search
        int pos = -1;     // default: not found

        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == key) {
                pos = i;
                break;
            }
        }

        if (pos != -1)
            System.out.println("Key found at index: " + pos);
        else
            System.out.println("Key not found");
    }
}

// Key found at index: 3

```

- `key` → element we want to search
- `pos` → stores location
- `break` → stops unnecessary comparisons


