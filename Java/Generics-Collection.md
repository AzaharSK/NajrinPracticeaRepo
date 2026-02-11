## Generics in Java:
- Generics were introduced in Java 5.
- They allow writing code and algorithms that work with any primitive wrapper or user-defined type—independent of a particular data type.
- Generics provide type safety, ensuring errors are caught at compile-time, avoiding ClassCastException at runtime.
- They can be used to define classes, interfaces, and methods, making code reusable and type-independent.
- Promotes code reusability: the same class or method can operate on multiple data types.
- Eliminates the need for explicit casting of objects.

✅ In short: Generics make Java code safer, cleaner, and more flexible.

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
