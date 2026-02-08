```java
import java.util.Scanner;

public class OddEven {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        
        System.out.print("Enter a number: ");
        int num = sc.nextInt();

        if (num % 2 == 0)
            System.out.println("Even");
        else
            System.out.println("Odd");

        sc.close();
    }
}

```

#  CountDigits

```java
public class CountDigits {
    public static void main(String[] args) {

        int num = 375879;
        int n = num;
        int count = 0;

        while (n > 0) {
           
            n = n / 10;
            count++;
        }

        
        System.out.println(count);  //6
            
        
    }
}
```

# sum of all digits in a number code in java
```java
public class SumOfDigits {
    public static void main(String[] args) {

        int n = -37942;
        int sum = 0;
        int remainder;

        // Handle negative number
        if (n < 0) {
            n = -n;
        }

        // Extract digits and sum
        while (n > 0) {
            remainder = n % 10;
            sum = sum + remainder;
            n = n / 10;
        }

        System.out.println(sum);
    }
}

// (3 + 7 + 9 + 4 + 2 = 25)

```

# First Last Digit Sum
```java
public class FirstLastDigitSum {
    public static void main(String[] args) {

        int n = -37942;

        // If number is negative, make it positive
        if (n < 0) {
            n = -n;
        }

        // Last digit
        int ldigit = n % 10;
        System.out.println(ldigit);

        // Extract first digit
        while (n > 9) {
            n = n / 10;
        }

        int fdigit = n;
        System.out.println(fdigit);

        // Sum of first and last digit
        int sum = fdigit + ldigit;
        System.out.println(sum);
    }
}


```
```
ldigit = 2
fdigit = 3
sum = 5
```
# ArmstrongNumber
```java

public class ArmstrongNumber {
    public static void main(String[] args) {

        int num = 153;
        int n = num;
        int sum = 0;

        while (n > 0) {
            int r = n % 10;
            sum = sum + (r * r * r);
            n = n / 10;
        }

        if (sum == num) {   
            System.out.println("Armstrong number");
        } else {
            System.out.println("Not an Armstrong number");
        }
    }
}

// num == sum = 153 = (1x1x1) + (5x5x5) + (3x3x3)

```

# Palindrome number (121 → true)

```java
public class PalindromeNumber {
    public static void main(String[] args) {

        int num = 121;
        int n = num;
        int sum = 0;

        while (n > 0) {
            int r = n % 10;
            sum = (sum * 10) + r;
            n = n / 10;
        }

        System.out.println("Reverse = " + sum);

        if (sum == num) {
            System.out.println("Palindrome number");
        } else {
            System.out.println("Not a Palindrome");
        }
    }
}
```


# Factorial 

```java
public class FactorialNumber {
    public static void main(String[] args) {

        int num = 5;
        int fact = 1;

        for (int i = 1; i <= num; i++) {
            fact = fact * i;
        }

        System.out.println("Factorial = " + fact);  // Factorial = 120
    }
}
```

# Recursive Factorial

```java

public class FactorialRecursive {
    public static void main(String[] args) {

        int num = 5;
        int result = factorial(num);

        System.out.println("Factorial = " + result);
    }

    static int factorial(int n) {
        // Base case
        if (n == 0 || n == 1) {
            return 1;
        }
        // Recursive case
        return n * factorial(n - 1);
    }
}

```

```
factorial(5)
= 5 * factorial(4)
= 5 * 4 * factorial(3)
= 5 * 4 * 3 * 2 * 1 = 120
```
