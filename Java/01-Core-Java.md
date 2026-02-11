## The latest version of Java (as of 2025) ? - Important Features
- Java SE 25 (JDK 25) — released on September 16, 2025 

__Features :__

- #1  Java 25 (JDK 25) is the latest Long-Term Support (LTS) release in 2025.
- #2  Pattern Matching for primitives enhances instanceof and switch expressions.
- #3 Compact source files and instance main methods reduce boilerplate code.
- #4 Flexible constructor bodies allow statements before super() or this() calls.
- #5 Structured Concurrency simplifies multithreaded task management.
- #6 Scoped Values provide a safer alternative to ThreadLocal for sharing data.
- #7 Compact Object Headers reduce object memory footprint, improving JVM efficiency.
- #8 Ahead-of-Time (AOT) Method Profiling and enhanced Java Flight Recorder (JFR) improve startup performance and profiling capabilities.


## What is an Identifier in Java ?

- An identifier is the name given to a variable, method, class, interface, package, or object in Java.
- It is used to identify something in a program.

## What are reserved words ? How many reserved words in java ?

Reserved words (also called keywords) are words that have a special predefined meaning in Java.
You `cannot use` them as `identifier` like below:

- Variable names
- Class names
- Method names
- Interface names
- Package names

Because the `Java compiler` already understands them `as part of the java language syntax`.

### Java has 52 reserved words (keywords).

```java

abstract     assert       boolean      break        byte
case         catch        char         class        const*
continue     default      do           double       else
enum         extends      final        finally      float
for          goto*        if           implements   import
instanceof   int          interface    long         native
new          package      private      protected    public
return       short        static       strictfp     super
switch       synchronized this         throw        throws
transient    try          void         volatile     while
const        goto
```

## Data Types Supported in Java (With Size)

- Java data types are divided into 2 categories:
    - **Primitive Data Types (8 types)**
    -  **Non-Primitive (Reference) Data Types**

<img width="938" height="493" alt="image" src="https://github.com/user-attachments/assets/c4cb98ca-851c-4655-a65c-513f0d3439e5" />
<img width="989" height="836" alt="image" src="https://github.com/user-attachments/assets/f48ad646-41dc-4779-ac6c-dd9ff529bf91" />

## What are the Short-circuit operators in java
- Short-circuit operators are `logical operators` that stop evaluating the expression as soon as the result is determined.
- Java has two short-circuit operators:
    - __Logical AND__ → `&&`
    - __Logical OR__ → `||`

## What is difference in between == operator and .equal() method in java ?
- `==` compares object references (memory location), while `ob.equals()` compares the actual content of the String. For String comparison, `.equals()` should be used.

```sql
---------------------------------------------------------------------------------------------------
== Operator	                                    | .equals() Method
--------------------------------------------------------------------------------------------------
Compares memory reference (address)	            | Compares actual content (value)
Checks if two references point to same object	| Checks if values inside objects are equal
Works for primitive & objects	                | Mainly used for objects
---------------------------------------------------------------------------------------------------

```

```java
String s1 = new String("Java");
String s2 = new String("Java");

System.out.println(s1 == s2);   // false   // Two different objects are created in heap with diffrent refs memory address

System.out.println(s1.equals(s2));   // true  // Content same
```

## what is instance of operator in Java ?
- The instanceof operator is used to check whether an object is an instance of a specific class, subclass, or interface.
- It returns boolean type:
    - `true` → if the object belongs to that type
    - `false` → otherwise

```java

class Animal { }
class Dog extends Animal { }

public class Main {
    public static void main(String[] args) {
        Dog d = new Dog();

        System.out.println(d instanceof Dog);      // true
        System.out.println(d instanceof Animal);   // true
    }
}

// Example 2: Returns False

Animal a = new Animal();
System.out.println(a instanceof Dog);   // false
```
- Used mainly in inheritance and polymorphism
- Works only with objects (not primitives)
- Returns `false` if object is `null`


## What are tpes of type-casting supported in JAVA
- Type casting is the process of converting one data type into another data type.
- In Java, there are two types of type casting:

        - Widening / Implicit automatic Casting
        - Narrowing / Explicit manual Casting

  - Java also supports object casting through `upcasting` and `downcasting` of objects relared through inheritance.
    
<img width="1422" height="279" alt="image" src="https://github.com/user-attachments/assets/2fe3428b-bf34-4f5a-b310-a3193dcb03ac" />

```java

///////////////////// Widening Casting / Implicit casting  /////////////////////////////////////
int num = 10;
double d = num;   // automatic casting
System.out.println(d);   // 10.0

//✅ No data loss
//✅ No need to write cast manually

///////////////////// Narrowing Casting / Explicit casting  /////////////////////////////////////
int x = 130;
byte b = (byte) x;   // Need explicitely casting

System.out.println(b);  // -126

// Converting a larger data type into a smaller data type.  Data loss may occur
// Because byte range is -128 to 127 → overflow happens.
```
## What is object-oriented programming?
Object-Oriented Programming (OOP) is a programming paradigm based on the concept of __objects__, which contain:
```
Data (variables / fields)
Behavior (methods / functions)
```
In OOP, programs are designed by creating __classes__ and __objects__ that model real-world entities.

```Java
class Student {
    String name;     // data
    int age;

    void study() {   // behavior
        System.out.println("Studying...");
    }
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student();  // object creation
        s1.name = "Rahul";
        s1.age = 20;
        s1.study();
    }
}
```

- `Student` → Class
- `s1` → Object
- `name, age` → Data
- `study()` → Behavior

- OOP built on four main principles: `Encapsulation`, `Abstraction`, `Inheritance`, and `Polymorphism`.

What are the advantages of using C++?
What is a class?
What is an object?
