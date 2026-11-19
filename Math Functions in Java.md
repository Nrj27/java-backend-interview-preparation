# Some Useful Math Functions in Java

In Java, the `Math` class provides many built-in mathematical functions that are useful for solving programming and DSA practice problems.

You can use these functions directly using `Math.functionName()` without creating a Math object.

## 1. Basic Math Functions

| Function | Description |
| --- | --- |
| `Math.min(a, b)` | Returns the smallest value. |
| `Math.max(a, b)` | Returns the largest value. |
| `Math.abs(a)` | Returns the absolute value. |
| `Math.abs(a - b)` | Returns the absolute difference. |
| `Math.abs(a + b)` | Returns the absolute value of the sum. |
| `Math.signum(a)` | Returns the sign of a number as a float or double. |

## 2. Rounding Functions

| Function | Description |
| --- | --- |
| `Math.floor(a)` | Rounds down to the nearest integer (as a double). |
| `Math.ceil(a)` | Rounds up to the nearest integer (as a double). |
| `Math.round(a)` | Rounds to the nearest integer (returns `int` for float and `long` for double). |
| `Math.rint(a)` | Returns the nearest integer as a double. |
| `Math.round(a * 100.0) / 100.0` | Rounds to 2 decimal places approximately. |

## 3. Power and Square Root Functions

| Function | Description |
| --- | --- |
| `Math.pow(a, b)` | Returns a raised to the power b. |
| `Math.sqrt(a)` | Returns the square root. |
| `Math.cbrt(a)` | Returns the cube root. |
| `Math.hypot(a, b)` | Returns √(a² + b²). |

## 4. Division and Remainder

| Operator / Function | Description |
| --- | --- |
| `a % b` | Returns the remainder. |
| `a / b` | Performs division. |
| `Math.floorDiv(a, b)` | Returns the floor of integer division. |
| `Math.floorMod(a, b)` | Returns the floor-based remainder. |

Example:

java

```java
int a = 10;
int b = 3;

System.out.println(a / b);              // 3
System.out.println(a % b);              // 1
System.out.println(Math.floorDiv(a, b)); // 3
System.out.println(Math.floorMod(a, b)); // 1
```

## 5. Random Number Functions

| Function | Description |
| --- | --- |
| `Math.random()` | Generates a random double between 0.0 (inclusive) and 1.0 (exclusive). |
| `(int)(Math.random() * 10)` | Generates a random integer from 0 to 9. |
| `(int)(Math.random() * 100) + 1` | Generates a random integer from 1 to 100. |

## 6. Logarithmic Functions

| Function | Description |
| --- | --- |
| `Math.log(a)` | Natural logarithm (base e). |
| `Math.log10(a)` | Logarithm base 10. |
| `Math.log1p(a)` | Calculates log(1 + a) accurately for small values. |
| `Math.exp(a)` | Returns e raised to the power a. |
| `Math.expm1(a)` | Calculates e^a - 1 accurately for small values. |

## 7. Trigonometric Functions

| Function | Description |
| --- | --- |
| `Math.sin(a)` | Returns sine. |
| `Math.cos(a)` | Returns cosine. |
| `Math.tan(a)` | Returns tangent. |
| `Math.asin(a)` | Returns inverse sine. |
| `Math.acos(a)` | Returns inverse cosine. |
| `Math.atan(a)` | Returns inverse tangent. |
| `Math.atan2(y, x)` | Returns angle from coordinates. |
| `Math.toRadians(a)` | Converts degrees to radians. |
| `Math.toDegrees(a)` | Converts radians to degrees. |

Note: Trigonometric functions use radians.

## 8. Mathematical Constants

| Constant | Description |
| --- | --- |
| `Math.PI` | π (3.14159265...) |
| `Math.E` | Euler's number (2.71828182...) |
| `Math.sqrt(2)` | Square root of 2 |
| `Math.log(2)` | Natural logarithm of 2 |

## 9. Other Useful Math Functions

| Function | Description |
| --- | --- |
| `Math.addExact(a, b)` | Adds two integers and detects overflow. |
| `Math.subtractExact(a, b)` | Subtracts and detects overflow. |
| `Math.multiplyExact(a, b)` | Multiplies and detects overflow. |
| `Math.incrementExact(a)` | Increments by 1 and detects overflow. |
| `Math.decrementExact(a)` | Decrements by 1 and detects overflow. |
| `Math.negateExact(a)` | Negates a number and detects overflow. |
| `Math.toIntExact(a)` | Converts long to int and detects overflow. |

## 10. Complete Java Example

java

```java
public class Main {
    public static void main(String[] args) {

        int a = 10;
        int b = 3;

        System.out.println(Math.min(a, b));   // 3
        System.out.println(Math.max(a, b));   // 10
        System.out.println(Math.abs(a - b));  // 7
        System.out.println(Math.abs(a + b));  // 13

        System.out.println(a % b);            // 1

        System.out.println(Math.sqrt(a));     // 3.162...
        System.out.println(Math.pow(a, 2));   // 100.0
        System.out.println(Math.cbrt(a));     // 2.154...

        System.out.println(Math.floor(4.8));  // 4.0
        System.out.println(Math.ceil(4.2));   // 5.0
        System.out.println(Math.round(4.6));  // 5

        System.out.println(Math.PI);
        System.out.println(Math.random());
    }
}
```

## Most Important Functions for Java DSA

If you are preparing for coding interviews, focus on these first:

| Priority | Function |
| --- | --- |
| ⭐ | `Math.min(a, b)` |
| ⭐ | `Math.max(a, b)` |
| ⭐ | `Math.abs(a)` |
| ⭐ | `Math.sqrt(a)` |
| ⭐ | `Math.pow(a, b)` |
| ⭐ | `Math.floor(a)` |
| ⭐ | `Math.ceil(a)` |
| ⭐ | `Math.round(a)` |
| ⭐ | `Math.floorDiv(a, b)` |
| ⭐ | `Math.floorMod(a, b)` |
| ⭐ | `Math.random()` |

Important: Java integer division (`a / b`) removes the decimal part when both operands are integers. Also, `Math.pow()` returns a `double`, so type conversion may be needed when working with integers.
