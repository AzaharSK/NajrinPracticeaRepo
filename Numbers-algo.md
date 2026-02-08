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
        int result = fdigit + ldigit;
        System.out.println(result);
    }
}

```
