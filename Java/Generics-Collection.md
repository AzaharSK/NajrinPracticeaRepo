## Generics in Java:
- Generics are  Introduced in Java 5 - It enable you to write classes, interfaces, and methods that can operate on any type of object while providing compile-time type safety.
- It promotes `Code Reusability` – Same class/method can work with multiple data types.
- This is also `type-safe`, Errors are caught at `compile-time` and prevent `runtime ClassCastException`,
- No need to cast objects explicitly.


```java
// Generic class with one data member of type T

class Test<T> {
    private T data;  // single generic data member

    // Constructor
    public Test(T newdata) { this.data = newdata; }

    // Getter
    public T get() { return data; }
}

```
- `<T>` means this is a generic class/type.
-  Since `T` is a generic `type` parameter, `T data` can store any type depending on how the object is created.
- `<T>`type` parameter, will be replaced with a specific type, such as `Integer`, `String`, or even a custom class.
 when you create an object of this class.
- This shows the flexibility of generics: the same class can work with any type.

```java
Test<Integer> intTest = new Test<>(123);
System.out.println(intTest.get()); // Output: 123

Test<String> stringTest = new Test<>("Hello");
System.out.println(stringTest.get()); // Output: Hello

```

- `Test<Integer>` creates a Test object that stores an `Integer`.
- `Test<String>` creates a Test object that stores a `String`.
- This class is a generic wrapper around a single data member. It allows you to store and retrieve values of any type safely, without casting.

## Collection vs Collections :

- `Collection` → Interface (root for List, Set, Queue)
- `Collections` → Utility class with static methods (sort, reverse, shuffle)
