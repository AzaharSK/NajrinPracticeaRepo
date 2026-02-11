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
