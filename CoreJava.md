##  Abstract Class  vs Interface in Java:

```sql

| Abstract Class                                 | Interface                                                                 |
| ---------------------------------------------- | ------------------------------------------------------------------------- |
| Can have **abstract and non-abstract methods** | Methods are **abstract by default** (Java 8+ allows `default` & `static`) |
| Can have **instance variables**                | Variables are **public, static, final** by default                        |
| Supports **constructors**                      | ❌ No constructors                                                         |
| Supports **single inheritance**                | Supports **multiple inheritance**                                         |
| Can have **access modifiers**                  | Methods are **public by default**                                         |
| Uses `extends` keyword                         | Uses `implements` keyword                                                 |
| Can have method implementation                 | Focuses on **what to do**, not how                                        |

```

````
##  1. What is Java?

Theory:
Java is a high-level, object-oriented, platform-independent programming language.

Code:

class Hello {
    public static void main(String[] args) {
        System.out.println("Hello Java");
    }
}

## 2. Why is Java platform-independent?

Theory:
Java code compiles into bytecode, which runs on the JVM regardless of OS.

Code:

Java Source → Bytecode → JVM → Any OS

## 3. What is JVM?

Theory:
JVM executes bytecode and handles memory, GC, and runtime.

Code:

System.out.println("Executed by JVM");

## 4. Difference between JDK, JRE, JVM?

Theory:

JVM: Runs bytecode

JRE: JVM + libraries

JDK: JRE + dev tools

Code:

javac → JDK
java  → JRE

## 5. What are Java features?

Theory:
OOP, portable, secure, robust, multithreaded.

## 6. What is a class?

Theory:
Blueprint of an object.

Code:

class Car {
    String color;
}

## 7. What is an object?

Theory:
Instance of a class.

Code:

Car c = new Car();

## 8. What is Encapsulation?

Theory:
Wrapping data and methods, hiding data using private access.

Code:

class User {
    private String name;
    public String getName() {
        return name;
    }
}

## 9. What is Inheritance?

Theory:
One class acquires properties of another.

Code:

class Animal {
    void eat() {}
}
class Dog extends Animal {}

## 10. What is Polymorphism?

Theory:
Same method name, different behavior.

Code:

class A {
    void show() { System.out.println("A"); }
}
class B extends A {
    void show() { System.out.println("B"); }
}

## 11. Compile-time vs Runtime polymorphism?

Theory:

Compile-time: Method overloading

Runtime: Method overriding

Code:

int add(int a, int b) {}
double add(double a, double b) {}

## 12. What is Abstraction?

Theory:
Hiding implementation details.

Code:

abstract class Shape {
    abstract void draw();
}

## 13. Abstract class vs Interface?

Theory:
Interface supports multiple inheritance; abstract class does not.

Code:

interface A { void show(); }
abstract class B { abstract void display(); }

## 14. What is a constructor?

Theory:
Used to initialize objects.

Code:

class Test {
    Test() {
        System.out.println("Constructor");
    }
}

## 15. Can constructors be overloaded?

Theory:
Yes, multiple constructors with different parameters.

Code:

Test() {}
Test(int a) {}

## 16. What is this keyword?

Theory:
Refers to current object.

Code:

this.name = name;
```
