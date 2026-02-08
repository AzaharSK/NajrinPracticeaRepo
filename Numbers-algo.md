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



```
