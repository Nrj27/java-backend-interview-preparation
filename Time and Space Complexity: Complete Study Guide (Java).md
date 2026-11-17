# Time and Space Complexity: Complete Study Guide (Java)

Time and space complexity are two fundamental concepts in Data Structures and Algorithms (DSA). They help us analyze how efficiently an algorithm performs as the input size increases.

- Time Complexity: Measures how the execution time of an algorithm grows with input size.
- Space Complexity: Measures how the memory consumption of an algorithm grows with input size.

Both are expressed using Big O notation.

The goal is to write code that not only works but also performs efficiently when the input becomes large.

# 1. Understanding Time and Space Complexity

Suppose an algorithm receives an array containing `n` elements.

```java
int[] arr = {10, 20, 30, 40, 50};
```

Here:

$$
n=5
$$

When the input grows from 5 elements to 1,000 or 1,000,000 elements, we want to understand:

1. How much longer will the algorithm take?
2. How much additional memory will it require?

These questions are answered by time and space complexity.

## 1.1 Time Complexity

Time complexity describes how the number of operations performed by an algorithm grows with input size.

Example:

```java
public class Main {
    public static void printArray(int[] arr) {
        for (int num : arr) {
            System.out.println(num);
        }
    }
}
```

If the array contains:

- 5 elements → 5 iterations.
- 100 elements → 100 iterations.
- 1,000 elements → 1,000 iterations.

Therefore:

$$
T(n)=O(n)
$$

This is called linear time complexity.

## 1.2 Space Complexity

Space complexity describes how much memory an algorithm requires as input size grows.

Example:

```java
public class Main {
    public static int[] createArray(int n) {
        int[] result = new int[n];

        for (int i = 0; i < n; i++) {
            result[i] = i;
        }

        return result;
    }
}
```

The algorithm creates a new array containing `n` elements.

Therefore:

$$
S(n)=O(n)
$$

This is called linear space complexity.

# 2. Big O Notation

Big O notation describes the asymptotic upper bound of an algorithm's growth.

It helps us compare algorithms without depending on:

- Processor speed.
- Programming language.
- Compiler optimization.
- Operating system.
- Hardware configuration.

For example:

$$
T(n)=3n^2+5n+10
$$

We ignore constant multipliers and lower-order terms.

Therefore:

$$
\boxed{T(n)=O(n^2)}
$$

## 2.1 Rules for Simplifying Big O

| Rule | Example | Result |
| --- | --- | --- |
| Drop constants | $O(5n)$ | $O(n)$ |
| Drop lower-order terms | $O(n^2+n)$ | $O(n^2)$ |
| Add sequential operations | $O(n)+O(n)$ | $O(n)$ |
| Multiply nested operations | $O(n)\times O(n)$ | $O(n^2)$ |
| Ignore constant-time operations | $O(n+100)$ | $O(n)$ |

Important: Big O describes growth, not the exact number of seconds or bytes consumed.

# 3. Types of Time and Space Complexity

The following complexities are arranged from lower growth to higher growth.

## 3.1 Complexity Growth Hierarchy

From most efficient to least efficient:

$$
\boxed{
O(1)<O(\log n)<O(\sqrt n)<O(n)<O(n\log n)<O(n^2)<O(n^3)<O(2^n)<O(n!)
}
$$

| Complexity | Name | Growth Behavior |
| --- | --- | --- |
| $O(1)$ | Constant | Remains fixed |
| $O(\log n)$ | Logarithmic | Grows very slowly |
| $O(\sqrt n)$ | Square Root | Grows with square root of input |
| $O(n)$ | Linear | Grows proportionally to input |
| $O(n\log n)$ | Linearithmic | Linear growth multiplied by logarithmic growth |
| $O(n^2)$ | Quadratic | Grows with square of input |
| $O(n^3)$ | Cubic | Grows with cube of input |
| $O(2^n)$ | Exponential | Doubles with every additional input element |
| $O(n!)$ | Factorial | Grows extremely rapidly |

## 3.2 O(1) — Constant Complexity

The algorithm performs a fixed amount of work or uses a fixed amount of auxiliary memory, regardless of input size.

Time example:

```java
public class Main {
    public static int getFirst(int[] arr) {
        return arr[0];
    }
}
```

The algorithm accesses only one element.

$$
T(n)=O(1)
$$

Space example:

```java
public class Main {
    public static int calculateSum(int a, int b) {
        int result = a + b;
        return result;
    }
}
```

Only a fixed number of variables are used.

$$
S(n)=O(1)
$$

Common examples:

- Array index access.
- Swapping two variables.
- Mathematical calculations.
- Two-pointer operations using a fixed number of pointers.

## 3.3 O(log n) — Logarithmic Complexity

The problem size is reduced by a constant factor at every step.

Time example: Binary Search

```java
public class Main {
    public static int binarySearch(int[] arr, int target) {
        int low = 0;
        int high = arr.length - 1;

        while (low <= high) {
            int mid = low + (high - low) / 2;

            if (arr[mid] == target) {
                return mid;
            } else if (arr[mid] < target) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }

        return -1;
    }
}
```

At every iteration, approximately half of the search space is eliminated.

$$
n,\frac n2,\frac n4,\frac n8,\ldots,1
$$

The number of iterations is:

$$
\log_2 n
$$

Therefore:

$$
T(n)=O(\log n)
$$

Space example: Recursive Binary Search

```java
public class Main {
    public static int binarySearch(int[] arr, int low,
                                   int high, int target) {

        if (low > high) {
            return -1;
        }

        int mid = low + (high - low) / 2;

        if (arr[mid] == target) {
            return mid;
        }

        if (arr[mid] < target) {
            return binarySearch(arr, mid + 1, high, target);
        }

        return binarySearch(arr, low, mid - 1, target);
    }
}
```

Each recursive call halves the problem.

- Time: $O(\log n)$
- Auxiliary space: $O(\log n)$, because of the recursion stack.

Common examples:

- Binary Search.
- Balanced Binary Search Tree operations.
- Divide-and-conquer recursion with logarithmic depth.

## 3.4 O(√n) — Square Root Complexity

The number of operations grows proportionally to the square root of the input.

Example: Checking Prime Numbers

```java
public class Main {
    public static boolean isPrime(int n) {
        if (n <= 1) {
            return false;
        }

        for (int i = 2; i <= Math.sqrt(n); i++) {
            if (n % i == 0) {
                return false;
            }
        }

        return true;
    }
}
```

We only need to check divisors up to the square root of `n`.

$$
T(n)=O(\sqrt n)
$$

Auxiliary space:

$$
S(n)=O(1)
$$

Common examples:

- Trial division primality testing.
- Square-root-based search strategies.
- Certain block decomposition algorithms.

## 3.5 O(n) — Linear Complexity

The algorithm processes each element once or allocates memory proportional to the input size.

Time example:

```java
public class Main {
    public static int findMax(int[] arr) {
        int maximum = arr[0];

        for (int num : arr) {
            if (num > maximum) {
                maximum = num;
            }
        }

        return maximum;
    }
}
```

Each element is checked once.

$$
T(n)=O(n)
$$

Space example:

```java
public class Main {
    public static int[] copyArray(int[] arr) {
        int[] result = new int[arr.length];

        for (int i = 0; i < arr.length; i++) {
            result[i] = arr[i];
        }

        return result;
    }
}
```

A new array of size `n` is created.

$$
S(n)=O(n)
$$

Common examples:

- Array traversal.
- Linear Search.
- HashMap creation.
- Queue storage.
- One-dimensional Dynamic Programming.

## 3.6 O(n log n) — Linearithmic Complexity

This complexity commonly occurs in efficient sorting algorithms.

Examples:

- Merge Sort.
- Heap Sort.
- Average-case Quick Sort.

Example: Merge Sort

```java
public class Main {

    public static void mergeSort(int[] arr, int left, int right) {
        if (left >= right) {
            return;
        }

        int mid = left + (right - left) / 2;

        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);

        merge(arr, left, mid, right);
    }

    public static void merge(int[] arr, int left,
                             int mid, int right) {

        int[] temp = new int[right - left + 1];

        int i = left;
        int j = mid + 1;
        int k = 0;

        while (i <= mid && j <= right) {
            if (arr[i] <= arr[j]) {
                temp[k++] = arr[i++];
            } else {
                temp[k++] = arr[j++];
            }
        }

        while (i <= mid) {
            temp[k++] = arr[i++];
        }

        while (j <= right) {
            temp[k++] = arr[j++];
        }

        for (int x = 0; x < temp.length; x++) {
            arr[left + x] = temp[x];
        }
    }
}
```

Time complexity:

$$
T(n)=O(n\log n)
$$

Auxiliary space:

$$
S(n)=O(n)
$$

## 3.7 O(n²) — Quadratic Complexity

Quadratic complexity commonly occurs when two nested loops each process up to `n` elements.

Example:

```java
public class Main {
    public static void printPairs(int[] arr) {
        int n = arr.length;

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                System.out.println(arr[i] + ", " + arr[j]);
            }
        }
    }
}
```

Total operations:

$$
n\times n=n^2
$$

Therefore:

$$
T(n)=O(n^2)
$$

If we store an `n × n` matrix:

$$
S(n)=O(n^2)
$$

Common examples:

- Bubble Sort.
- Selection Sort.
- Comparing every pair.
- Two-dimensional DP tables.
- Adjacency matrices.

## 3.8 O(n³) — Cubic Complexity

Three nested loops commonly produce cubic complexity.

Example:

```java
public class Main {
    public static void printTriplets(int[] arr) {
        int n = arr.length;

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                for (int k = 0; k < n; k++) {
                    System.out.println(i + " " + j + " " + k);
                }
            }
        }
    }
}
```

Total operations:

$$
n\times n\times n=n^3
$$

Therefore:

$$
T(n)=O(n^3)
$$

Common examples:

- Basic matrix multiplication.
- Floyd-Warshall algorithm.
- Triple nested-loop problems.

## 3.9 O(2ⁿ) — Exponential Complexity

The number of operations doubles with each additional input element.

Example: Generating All Subsets

```java
import java.util.*;

public class Main {

    public static void generateSubsets(
            int[] arr, int index, List<Integer> current) {

        if (index == arr.length) {
            System.out.println(current);
            return;
        }

        // Exclude current element
        generateSubsets(arr, index + 1, current);

        // Include current element
        current.add(arr[index]);

        generateSubsets(arr, index + 1, current);

        current.remove(current.size() - 1);
    }
}
```

Each element has two choices:

- Include the element.
- Exclude the element.

Total subsets:

$$
2^n
$$

Therefore:

$$
T(n)=O(2^n)
$$

Auxiliary recursion space:

$$
S(n)=O(n)
$$

Common examples:

- Subset generation.
- Brute-force recursive Fibonacci.
- Certain backtracking algorithms.

## 3.10 O(n\!) — Factorial Complexity

Factorial complexity occurs when an algorithm generates or explores all possible permutations.

Example: Generating Permutations

```java
import java.util.*;

public class Main {

    public static void generatePermutations(
            int[] arr, int index) {

        if (index == arr.length) {
            System.out.println(Arrays.toString(arr));
            return;
        }

        for (int i = index; i < arr.length; i++) {

            swap(arr, index, i);

            generatePermutations(arr, index + 1);

            swap(arr, index, i);
        }
    }

    public static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
}
```

Number of permutations:

$$
n!=n(n-1)(n-2)\cdots1
$$

Generating all permutations requires:

$$
T(n)=O(n\cdot n!)
$$

when accounting for the cost of printing each permutation.

Auxiliary recursion space:

$$
S(n)=O(n)
$$

Common examples:

- Generating permutations.
- Brute-force Traveling Salesperson Problem.
- Exhaustive ordering problems.

# 4. Time Complexity vs Space Complexity

Although both concepts measure algorithm efficiency, they measure different resources.

| Feature | Time Complexity | Space Complexity |
| --- | --- | --- |
| Measures | Execution work | Memory usage |
| Focus | Number of operations | Memory allocation |
| Depends on | Input size | Input size |
| Common notation | Big O | Big O |
| Optimization | Reduce operations | Reduce extra memory |
| Example | Binary Search: $O(\log n)$ | New array: $O(n)$ |

## Example: One Algorithm, Two Complexities

```java
public class Main {

    public static int[] squareArray(int[] arr) {
        int[] result = new int[arr.length];

        for (int i = 0; i < arr.length; i++) {
            result[i] = arr[i] * arr[i];
        }

        return result;
    }
}
```

Time analysis:

- Loop runs `n` times.
- Each iteration performs constant-time work.

$$
T(n)=O(n)
$$

Space analysis:

- A new array is created.
- It stores `n` elements.

$$
S(n)=O(n)
$$

Final complexity:

- Time: $O(n)$
- Auxiliary space: $O(n)$

# 5. Types of Space Complexity

Space complexity needs special attention because input memory and additional memory are different.

## 5.1 Input Space

Memory occupied by the original input.

Example:

```java
public class Main {

    public static int process(int[] arr) {
        return arr[0];
    }
}
```

If the input array contains `n` elements, its storage is:

$$
O(n)
$$

## 5.2 Auxiliary Space

Extra memory used by the algorithm, excluding the original input.

Example:

```java
public class Main {

    public static int findSum(int[] arr) {
        int total = 0;

        for (int num : arr) {
            total += num;
        }

        return total;
    }
}
```

The algorithm uses only one additional variable.

$$
S_{\text{aux}}(n)=O(1)
$$

## 5.3 Total Space Complexity

Total space includes input storage and auxiliary storage.

$$
S_{\text{total}}(n)
=
S_{\text{input}}(n)+S_{\text{aux}}(n)
$$

For the previous example:

$$
S_{\text{total}}(n)=O(n)+O(1)
$$

$$
\boxed{S_{\text{total}}(n)=O(n)}
$$

Important interview distinction: When someone asks for space complexity, clarify whether they mean auxiliary space or total space. In DSA interviews, auxiliary space is frequently the intended metric.

# 6. How to Identify Time Complexity in Java Code

The easiest way is to count how many times the important statements execute.

## Case 1: Single Loop

```java
for (int i = 0; i < n; i++) {
    System.out.println(i);
}
```

Iterations:

$$
n
$$

Complexity:

$$
O(n)
$$

## Case 2: Two Separate Loops

```java
for (int i = 0; i < n; i++) {
    System.out.println(i);
}

for (int j = 0; j < n; j++) {
    System.out.println(j);
}
```

Total operations:

$$
n+n=2n
$$

Complexity:

$$
O(n)
$$

## Case 3: Nested Loops

```java
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        System.out.println(i + " " + j);
    }
}
```

Total operations:

$$
n\times n=n^2
$$

Complexity:

$$
O(n^2)
$$

## Case 4: Loop Dividing by Two

```java
int i = n;

while (i > 1) {
    i = i / 2;
}
```

Iterations:

$$
\log_2 n
$$

Complexity:

$$
O(\log n)
$$

## Case 5: Loop Multiplying by Two

```java
int i = 1;

while (i < n) {
    i = i * 2;
}
```

Iterations:

$$
O(\log n)
$$

## Case 6: Nested Loop with Different Bounds

```java
for (int i = 0; i < n; i++) {
    for (int j = 0; j < i; j++) {
        System.out.println(i + " " + j);
    }
}
```

Total iterations:

$$
0+1+2+\cdots+(n-1)
$$

$$
=\frac{n(n-1)}{2}
$$

Therefore:

$$
O(n^2)
$$

## Case 7: Loop Inside a Logarithmic Loop

```java
int i = 1;

while (i < n) {

    for (int j = 0; j < n; j++) {
        System.out.println(j);
    }

    i *= 2;
}
```

The outer loop executes $O(\log n)$ times.

The inner loop executes $O(n)$ times.

Therefore:

$$
\boxed{O(n\log n)}
$$

## Case 8: Recursive Function

```java
public static int factorial(int n) {

    if (n <= 1) {
        return 1;
    }

    return n * factorial(n - 1);
}
```

The function calls itself `n` times.

Time:

$$
O(n)
$$

Recursion stack:

$$
O(n)
$$

# 7. How to Identify Space Complexity in Java Code

Focus on memory allocations and recursion depth.

| Java Code Pattern | Auxiliary Space |
| --- | --- |
| Fixed variables | $O(1)$ |
| `new int[n]` | $O(n)$ |
| `new ArrayList<>()` storing n elements | $O(n)$ |
| `new HashMap<>()` storing n elements | $O(n)$ |
| Recursion depth n | $O(n)$ |
| Recursion depth log n | $O(\log n)$ |
| `new int[n][n]` | $O(n^2)$ |
| Fixed-size queue | $O(1)$ |

### Example 1: Constant Space

```java
public static int add(int a, int b) {
    int sum = a + b;
    return sum;
}
```

$$
S(n)=O(1)
$$

### Example 2: Linear Space

```java
public static int[] createArray(int n) {
    int[] result = new int[n];

    for (int i = 0; i < n; i++) {
        result[i] = i;
    }

    return result;
}
```

$$
S(n)=O(n)
$$

### Example 3: Quadratic Space

```java
public static int[][] createMatrix(int n) {
    int[][] matrix = new int[n][n];

    return matrix;
}
```

$$
S(n)=O(n^2)
$$

### Example 4: Recursive Space

```java
public static void countDown(int n) {

    if (n == 0) {
        return;
    }

    countDown(n - 1);
}
```

Maximum recursion depth:

$$
n
$$

Therefore:

$$
S(n)=O(n)
$$

# 8. Best, Average and Worst Case Complexity

An algorithm may behave differently depending on the input.

Consider Linear Search:

```java
public class Main {

    public static int search(int[] arr, int target) {

        for (int i = 0; i < arr.length; i++) {

            if (arr[i] == target) {
                return i;
            }
        }

        return -1;
    }
}
```

| Case | Situation | Time Complexity |
| --- | --- | --- |
| Best case | Element is at the first position | $O(1)$ |
| Average case | Element is somewhere in the middle | $O(n)$ |
| Worst case | Element is last or absent | $O(n)$ |

### Understanding the Three Cases

- Best Case: Minimum number of operations required.
- Average Case: Expected number of operations over an assumed input distribution.
- Worst Case: Maximum number of operations for an input of size `n`.

Worst-case complexity is commonly used in coding interviews because it provides a useful upper-bound guarantee.

# 9. Common Java Data Structures and Their Complexity

The following table provides typical operation complexities.

| Data Structure | Access | Search | Insertion | Deletion |
| --- | --- | --- | --- | --- |
| Array | O(1) | O(n) | O(n) | O(n) |
| ArrayList | O(1) | O(n) | O(1)\* | O(n) |
| LinkedList | O(n) | O(n) | O(1)\*\* | O(1)\*\* |
| Stack (ArrayDeque) | O(n)\*\*\* | O(n) | O(1) | O(1) |
| Queue (ArrayDeque) | O(n)\*\*\* | O(n) | O(1) | O(1) |
| HashMap | N/A | O(1)\* | O(1)\* | O(1)\* |
| HashSet | N/A | O(1)\* | O(1)\* | O(1)\* |
| TreeMap | N/A | O(log n) | O(log n) | O(log n) |
| PriorityQueue | O(1)\*\*\*\* | O(n) | O(log n) | O(log n) |

Notes:

- `*` ArrayList append is amortized O(1); HashMap and HashSet operations are typically expected O(1).
- `**` LinkedList insertion/deletion is O(1) when the relevant node or position is already known.
- `***` Arbitrary element access is O(n); access to the stack top or queue front is O(1).
- `****` PriorityQueue provides O(1) access to the minimum element.

# 10. Sorting Algorithms and Their Complexity

| Algorithm | Best Case | Average Case | Worst Case | Auxiliary Space |
| --- | --- | --- | --- | --- |
| Bubble Sort | O(n)\* | O(n²) | O(n²) | O(1) |
| Selection Sort | O(n²) | O(n²) | O(n²) | O(1) |
| Insertion Sort | O(n) | O(n²) | O(n²) | O(1) |
| Merge Sort | O(n log n) | O(n log n) | O(n log n) | O(n) |
| Quick Sort | O(n log n) | O(n log n) | O(n²) | O(log n)\*\* |
| Heap Sort | O(n log n) | O(n log n) | O(n log n) | O(1) |

Notes:

- `*` Bubble Sort achieves O(n) best-case time with an early-exit optimization.
- `**` Quick Sort typically uses O(log n) recursion stack on average, but can reach O(n) in the worst case.

## Java Sorting Example

```java
import java.util.Arrays;

public class Main {
    public static void main(String[] args) {

        int[] arr = {5, 2, 8, 1, 3};

        Arrays.sort(arr);

        System.out.println(Arrays.toString(arr));
    }
}
```

For primitive arrays, Java's `Arrays.sort()` uses an optimized Dual-Pivot Quicksort implementation.

# 11. Searching Algorithms and Their Complexity

| Algorithm | Best Case | Average Case | Worst Case | Auxiliary Space |
| --- | --- | --- | --- | --- |
| Linear Search | O(1) | O(n) | O(n) | O(1) |
| Binary Search (Iterative) | O(1) | O(log n) | O(log n) | O(1) |
| Binary Search (Recursive) | O(1) | O(log n) | O(log n) | O(log n) |
| HashMap Search | O(1) | O(1) expected | O(n) theoretical | O(1) additional per lookup |

Note: Binary Search requires sorted data and efficient indexed access, such as an array.

# 12. Choosing an Algorithm Based on Input Size

In coding interviews and competitive programming, input size often determines which algorithm is practical.

The following table is a rough guideline, not a guarantee. Actual limits depend on the language, hardware, implementation, and time limit.

| Input Size | Common Target Complexity | Suitable Techniques |
| --- | --- | --- |
| n ≤ 10 | O(n\!) or O(2ⁿ) | Backtracking, permutations |
| n ≤ 20 | O(2ⁿ) | Bitmasking, subset DP |
| n ≤ 500 | O(n³) | Floyd-Warshall, cubic DP |
| n ≤ 5,000 | O(n²) | Nested loops, pair comparisons |
| n ≤ 10⁵ | O(n log n) or O(n) | Sorting, hashing, two pointers |
| n ≤ 10⁶ | O(n) or O(n log n) | Linear traversal, optimized sorting |
| n \> 10⁶ | Usually O(n) or better | Efficient scanning, mathematical methods |

For example, if:

$$
n=10^6
$$

Then:

- $O(n)$ requires approximately 1 million operations.
- $O(n\log_2 n)$ requires approximately 20 million operation-scale work.
- $O(n^2)$ requires approximately 1 trillion operations.

This explains why algorithm selection is important.

# 13. Time-Space Trade-Off

Time and space optimization often involve making one resource more expensive to improve the other.

## Example: Finding Duplicate Elements

### Approach 1: Nested Loops

```java
public class Main {

    public static boolean hasDuplicate(int[] arr) {

        int n = arr.length;

        for (int i = 0; i < n; i++) {

            for (int j = i + 1; j < n; j++) {

                if (arr[i] == arr[j]) {
                    return true;
                }
            }
        }

        return false;
    }
}
```

- Time: $O(n^2)$
- Auxiliary space: $O(1)$

### Approach 2: Using HashSet

```java
import java.util.HashSet;

public class Main {

    public static boolean hasDuplicate(int[] arr) {

        HashSet<Integer> seen = new HashSet<>();

        for (int num : arr) {

            if (seen.contains(num)) {
                return true;
            }

            seen.add(num);
        }

        return false;
    }
}
```

- Expected time: $O(n)$
- Auxiliary space: $O(n)$

| Approach | Time | Auxiliary Space |
| --- | --- | --- |
| Nested loops | O(n²) | O(1) |
| HashSet | O(n) expected | O(n) |

The second approach uses additional memory to improve execution time.

This is called the time-space trade-off.

# 14. Common Mistakes in Complexity Analysis

1. Assuming every nested loop is O(n²).
   Not always. The inner loop may run a logarithmic number of times or have a different bound.
2. Adding complexities of sequential loops incorrectly.
   $O(n)+O(n)=O(n)$, not $O(n^2)$.
3. Ignoring recursive stack memory.
   Recursive calls consume memory even when no new arrays are created.
4. Confusing total space with auxiliary space.
   Input memory and additional algorithm memory are different.
5. Assuming HashMap operations are always O(1).
   They are generally expected O(1), but worst-case lookup can be O(n).
6. Assuming in-place means no memory usage.
   In-place algorithms can still use variables and recursion stacks.
7. Assuming faster time always means better.
   Memory limits, implementation complexity, and input constraints also matter.
8. Treating Big O as exact runtime.
   Two O(n) algorithms can have very different actual execution times.

# 15. Practical Optimization Techniques

| Technique | Main Benefit | Typical Complexity Improvement |
| --- | --- | --- |
| HashMap / HashSet | Faster lookup | O(n²) → O(n) |
| Two Pointers | Avoid repeated comparisons | O(n²) → O(n) |
| Sliding Window | Avoid recalculating subarrays | O(n²) → O(n) |
| Binary Search | Reduce search space | O(n) → O(log n) |
| Sorting | Enable efficient searching | Repeated O(n) searches → O(n log n) preprocessing + O(log n) per search |
| Memoization | Avoid repeated calculations | Exponential → Polynomial in many problems |
| Tabulation | Store previously computed results | Avoid repeated recursive work |
| In-place Operations | Reduce extra memory | O(n) → O(1) auxiliary space in suitable problems |

# 16. Quick Revision Cheat Sheet

## Time Complexity

| Complexity | Common Pattern |
| --- | --- |
| O(1) | Direct access |
| O(log n) | Halving the input |
| O(√n) | Checking up to square root |
| O(n) | Single traversal |
| O(n log n) | Efficient sorting |
| O(n²) | Two nested loops |
| O(n³) | Three nested loops |
| O(2ⁿ) | Binary branching recursion |
| O(n\!) | All permutations |

## Space Complexity

| Complexity | Common Pattern |
| --- | --- |
| O(1) | Fixed variables |
| O(log n) | Logarithmic recursion depth |
| O(n) | Array, set, map, linear stack |
| O(n²) | Matrix or 2D DP |
| O(2ⁿ) | Storing all subsets |
| O(n\!) | Storing all permutations |

# 17. Practice Questions

Test your understanding by identifying the time and auxiliary space complexity of each Java code snippet.

## Question 1: Single Loop

```java
for (int i = 0; i < n; i++) {
    System.out.println(i);
}
```

What is the time complexity?

- A. O(1)
- B. O(log n)
- C. O(n)
- D. O(n²)

Answer: C. O(n)

Explanation: The loop executes `n` times.

## Question 2: Nested Loops

```java
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        System.out.println(i + " " + j);
    }
}
```

What is the time complexity?

- A. O(n)
- B. O(n log n)
- C. O(n²)
- D. O(n³)

Answer: C. O(n²)

Explanation: Two nested loops each execute `n` times.

## Question 3: Logarithmic Loop

```java
int i = 1;

while (i < n) {
    i *= 2;
}
```

What is the time complexity?

- A. O(1)
- B. O(log n)
- C. O(n)
- D. O(n²)

Answer: B. O(log n)

Explanation: The value doubles during each iteration.

## Question 4: Constant Auxiliary Space

```java
public static int findSum(int[] arr) {

    int total = 0;

    for (int num : arr) {
        total += num;
    }

    return total;
}
```

What is the auxiliary space complexity?

- A. O(1)
- B. O(log n)
- C. O(n)
- D. O(n²)

Answer: A. O(1)

Explanation: Only a fixed number of variables are used.

## Question 5: Linear Auxiliary Space

```java
public static int[] createArray(int n) {

    int[] result = new int[n];

    return result;
}
```

What is the auxiliary space complexity?

- A. O(1)
- B. O(log n)
- C. O(n)
- D. O(n²)

Answer: C. O(n)

Explanation: A new array containing `n` elements is allocated.

## Question 6: Linearithmic Time

```java
for (int i = 1; i < n; i *= 2) {

    for (int j = 0; j < n; j++) {
        System.out.println(j);
    }
}
```

What is the time complexity?

- A. O(n)
- B. O(log n)
- C. O(n log n)
- D. O(n²)

Answer: C. O(n log n)

Explanation: The outer loop runs log n times, and the inner loop runs n times.

## Question 7: Different Nested Loop Bounds

```java
for (int i = 0; i < n; i++) {

    for (int j = 0; j < i; j++) {
        System.out.println(i + " " + j);
    }
}
```

What is the time complexity?

- A. O(n)
- B. O(log n)
- C. O(n²)
- D. O(2ⁿ)

Answer: C. O(n²)

Explanation: The total number of iterations is:

$$
\frac{n(n-1)}{2}=O(n^2)
$$

# 18. Final Takeaways

The most important principles to remember when solving DSA problems are:

1. Analyze before coding: Understand the expected input size and constraints before selecting an algorithm.
2. Focus on dominant growth: Ignore constants and lower-order terms when simplifying Big O.
3. Count loops carefully: Sequential loops add; nested loops multiply when their iteration counts are independent.
4. Account for recursion: Analyze both recursive execution time and call-stack memory.
5. Distinguish memory types: Understand input space, auxiliary space, and total space.
6. Use appropriate data structures: HashMaps, HashSets, Heaps, Queues, and Trees can significantly improve algorithm performance.
7. Balance time and space: Sometimes using additional memory is worthwhile to reduce execution time.
8. Consider real constraints: An algorithm must satisfy both time limits and memory limits.

## The Golden Rule

Efficient Algorithm = Good Time Complexity + Good Space Complexity

- Time complexity tells us how fast an algorithm scales.
- Space complexity tells us how much memory it needs.
- Big O helps us compare their growth as input size increases.

The ultimate goal is to choose an algorithm that is efficient, scalable, and suitable for the given constraints.
