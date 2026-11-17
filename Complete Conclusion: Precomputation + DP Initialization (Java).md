# Complete Conclusion: Precomputation + DP Initialization (Java)

This is your revision guide for initializing Precomputation and Dynamic Programming arrays in 1D, 2D and 3D.

## 1. Precomputation vs Dynamic Programming

| Precomputation | Dynamic Programming |
| --- | --- |
| Calculates information beforehand | Solves bigger problems using smaller subproblems |
| Stores reusable calculated values | Stores answers to subproblems |
| Avoids repeated calculations | Avoids repeated solving |
| Often uses 1D, 2D or 3D arrays | Often uses 1D, 2D or 3D arrays |

Remember: Both can use the same types of arrays. The difference is their purpose.

## 2. Precomputation initialization

Precomputation initialization depends on what you want to calculate.

### 1D array



```java
int[] pre = new int[n];
```

### 2D array



```java
int[][] pre = new int[n][m];
```

### 3D array



```java
int[][][] pre = new int[n][m][k];
```

Java automatically initializes:

- `int` arrays with `0`.
- `boolean` arrays with `false`.
- Object arrays with `null`.

If you need a different initial value, use `Arrays.fill()`.

Here is the complete Java code for Precomputation initialization, covering 1D, 2D and 3D arrays, with all values calculated and printed using `System.out.println()`.

We'll use simple examples:

- 1D: Store square of index.
- 2D: Store sum of two indices.
- 3D: Store sum of three indices.

## Complete Java code



```java

import java.util.Arrays;

public class Precomputation {

    public static void main(String[] args) {

        int n = 5;
        int m = 4;
        int k = 3;

        // =================================
        // 1. 1D PRECOMPUTATION
        // =================================

        int[] pre1D = new int[n];

        for (int i = 0; i < n; i++) {
            pre1D[i] = i * i;
        }


        // =================================
        // 2. 2D PRECOMPUTATION
        // =================================

        int[][] pre2D = new int[n][m];

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                pre2D[i][j] = i + j;
            }
        }


        // =================================
        // 3. 3D PRECOMPUTATION
        // =================================

        int[][][] pre3D = new int[n][m][k];

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                for (int z = 0; z < k; z++) {
                    pre3D[i][j][z] = i + j + z;
                }
            }
        }


        // =================================
        // 4. PRINT 1D ARRAY
        // =================================

        System.out.println("========== 1D PRECOMPUTATION ==========");

        System.out.println(Arrays.toString(pre1D));


        // =================================
        // 5. PRINT 2D ARRAY
        // =================================

        System.out.println("========== 2D PRECOMPUTATION ==========");

        for (int[] row : pre2D) {
            System.out.println(Arrays.toString(row));
        }


        // =================================
        // 6. PRINT 3D ARRAY
        // =================================

        System.out.println("========== 3D PRECOMPUTATION ==========");

        for (int[][] matrix : pre3D) {

            for (int[] row : matrix) {
                System.out.println(Arrays.toString(row));
            }

            System.out.println();
        }

    }
}
```

## Expected output



```text

========== 1D PRECOMPUTATION ==========
[0, 1, 4, 9, 16]

========== 2D PRECOMPUTATION ==========
[0, 1, 2, 3]
[1, 2, 3, 4]
[2, 3, 4, 5]
[3, 4, 5, 6]
[4, 5, 6, 7]

========== 3D PRECOMPUTATION ==========
[0, 1, 2]
[1, 2, 3]
[2, 3, 4]
[3, 4, 5]

[1, 2, 3]
[2, 3, 4]
[3, 4, 5]
[4, 5, 6]

[2, 3, 4]
[3, 4, 5]
[4, 5, 6]
[5, 6, 7]

[3, 4, 5]
[4, 5, 6]
[5, 6, 7]
[6, 7, 8]

[4, 5, 6]
[5, 6, 7]
[6, 7, 8]
[7, 8, 9]
```

## 3 important things to understand

1. 1D precomputation



```java
pre1D[i] = i * i;
```

We calculate and store one value for each index.

2. 2D precomputation



```java
pre2D[i][j] = i + j;
```

We calculate and store values for every combination of two indices.

3. 3D precomputation



```java
pre3D[i][j][z] = i + j + z;
```

We calculate and store values for every combination of three indices.

## Final comparison

| Concept | 1D | 2D | 3D |
| --- | --- | --- | --- |
| Precomputation | One loop | Two loops | Three loops |
| DP | One dimension | Two dimensions | Three dimensions |
| Access | `arr[i]` | `arr[i][j]` | `arr[i][j][k]` |

Remember: Precomputation does not have a fixed initialization value like minimum DP or maximum DP. You initialize the array according to the information you want to calculate and store.




# 3. DP initialization: All four patterns

### Pattern 1: Minimum problems

Examples:

- Minimum cost
- Minimum operations
- Minimum coins
- Shortest path

Initialize with `Integer.MAX_VALUE`.

1D

```java
int[] dp = new int[n];
Arrays.fill(dp, Integer.MAX_VALUE);
```

2D

```java
int[][] dp = new int[n][m];

for (int i = 0; i < n; i++) {
    Arrays.fill(dp[i], Integer.MAX_VALUE);
}
```

3D

```java
int[][][] dp = new int[n][m][k];

for (int i = 0; i < n; i++) {
    for (int j = 0; j < m; j++) {
        Arrays.fill(dp[i][j], Integer.MAX_VALUE);
    }
}
```

### Pattern 2: Maximum problems

Examples:

- Maximum profit
- Maximum score
- Maximum sum

Initialize with `Integer.MIN_VALUE`.

1D

```java
int[] dp = new int[n];
Arrays.fill(dp, Integer.MIN_VALUE);
```

2D

```java
int[][] dp = new int[n][m];

for (int i = 0; i < n; i++) {
    Arrays.fill(dp[i], Integer.MIN_VALUE);
}
```

3D

```java
int[][][] dp = new int[n][m][k];

for (int i = 0; i < n; i++) {
    for (int j = 0; j < m; j++) {
        Arrays.fill(dp[i][j], Integer.MIN_VALUE);
    }
}
```

### Pattern 3: Counting problems

Examples:

- Number of ways
- Number of paths
- Number of combinations

Initialize with `0`.

1D

```java
int[] dp = new int[n];
Arrays.fill(dp, 0);
```

2D

```java
int[][] dp = new int[n][m];

for (int i = 0; i < n; i++) {
    Arrays.fill(dp[i], 0);
}
```

3D

```java
int[][][] dp = new int[n][m][k];

for (int i = 0; i < n; i++) {
    for (int j = 0; j < m; j++) {
        Arrays.fill(dp[i][j], 0);
    }
}
```

### Pattern 4: Boolean problems

Examples:

- Subset sum
- Word break
- Reachability
- Can we achieve a target?

Initialize with `false`.

1D

```java
boolean[] dp = new boolean[n];
Arrays.fill(dp, false);
```

2D

```java
boolean[][] dp = new boolean[n][m];

for (int i = 0; i < n; i++) {
    Arrays.fill(dp[i], false);
}
```

3D

```java
boolean[][][] dp = new boolean[n][m][k];

for (int i = 0; i < n; i++) {
    for (int j = 0; j < m; j++) {
        Arrays.fill(dp[i][j], false);
    }
}
```

## 4. Complete initialization cheat sheet

## DP initialization reference

| Pattern | Initial value | Purpose |
| --- | --- | --- |
| Minimum | `Integer.MAX_VALUE` | Find smallest |
| Maximum | `Integer.MIN_VALUE` | Find largest |
| Counting | `0` | Count ways |
| Boolean | `false` | Check possibility |

## 5. Base case initialization

After initializing the array, set the known answers separately.

| Pattern | Example base case |
| --- | --- |
| Minimum | `dp[0] = 0` |
| Maximum | `dp[0] = 0` |
| Counting | `dp[0] = 1` |
| Boolean | `dp[0] = true` |

These are common examples, not universal rules. Always decide base cases based on what your DP state represents.

## 6. Important things to remember

Rule 1: Choose dimensions based on the information your state needs.

- One variable → 1D.
- Two variables → 2D.
- Three variables → 3D.

Rule 2: Choose initialization based on the problem.

- Minimum → Infinity.
- Maximum → Negative infinity.
- Counting → Zero.
- Boolean → False.

Rule 3: Initialize base cases separately.

Rule 4: Be careful with integer overflow.

For example:

```java
if (dp[i] != Integer.MAX_VALUE) {
    // Safe to add a cost, provided the result fits in int.
}
```

Rule 5: Don't blindly use infinity everywhere. Sometimes zero or another starting value is the correct initialization.

## 7. Your DP problem-solving checklist

Use this whenever you solve a new DP problem.

DP checklist


1. Understand what information needs to be stored.

2. Decide whether precomputation is useful.

3. Define what dp\[i\] or dp\[i\]\[j\] represents.

4. Choose 1D, 2D or 3D dimensions.

5. Identify whether the problem is minimum, maximum, counting or Boolean.

6. Initialize the array with the appropriate value.

7. Identify and initialize base cases.

8. Write the transition formula.

9. Decide the order in which states should be calculated.

10. Return the required DP state.


My final advice: Don't memorize only the initialization code. First understand what your DP state means. Once you understand the state, choosing the dimensions, initial values and base cases becomes much easier.



### DP Initialization Code 
Here is the complete Java code with `System.out.println()` statements to print all 1D, 2D and 3D arrays after initialization and base-case assignment.

```java

import java.util.Arrays;

public class DPInitialization {

    public static void main(String[] args) {

        int n = 5;
        int m = 4;
        int k = 3;

        // =================================
        // 1. MINIMUM DP
        // =================================

        int[] min1D = new int[n];
        Arrays.fill(min1D, Integer.MAX_VALUE);

        int[][] min2D = new int[n][m];
        for (int i = 0; i < n; i++) {
            Arrays.fill(min2D[i], Integer.MAX_VALUE);
        }

        int[][][] min3D = new int[n][m][k];
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                Arrays.fill(min3D[i][j], Integer.MAX_VALUE);
            }
        }

        // =================================
        // 2. MAXIMUM DP
        // =================================

        int[] max1D = new int[n];
        Arrays.fill(max1D, Integer.MIN_VALUE);

        int[][] max2D = new int[n][m];
        for (int i = 0; i < n; i++) {
            Arrays.fill(max2D[i], Integer.MIN_VALUE);
        }

        int[][][] max3D = new int[n][m][k];
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                Arrays.fill(max3D[i][j], Integer.MIN_VALUE);
            }
        }

        // =================================
        // 3. COUNTING DP
        // =================================

        int[] count1D = new int[n];
        Arrays.fill(count1D, 0);

        int[][] count2D = new int[n][m];
        for (int i = 0; i < n; i++) {
            Arrays.fill(count2D[i], 0);
        }

        int[][][] count3D = new int[n][m][k];
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                Arrays.fill(count3D[i][j], 0);
            }
        }

        // =================================
        // 4. BOOLEAN DP
        // =================================

        boolean[] bool1D = new boolean[n];
        Arrays.fill(bool1D, false);

        boolean[][] bool2D = new boolean[n][m];
        for (int i = 0; i < n; i++) {
            Arrays.fill(bool2D[i], false);
        }

        boolean[][][] bool3D = new boolean[n][m][k];
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                Arrays.fill(bool3D[i][j], false);
            }
        }

        // =================================
        // 5. BASE CASES
        // =================================

        // Minimum
        min1D[0] = 0;
        min2D[0][0] = 0;
        min3D[0][0][0] = 0;

        // Maximum
        max1D[0] = 0;
        max2D[0][0] = 0;
        max3D[0][0][0] = 0;

        // Counting
        count1D[0] = 1;
        count2D[0][0] = 1;
        count3D[0][0][0] = 1;

        // Boolean
        bool1D[0] = true;
        bool2D[0][0] = true;
        bool3D[0][0][0] = true;

        // =================================
        // 6. PRINT ALL ARRAYS
        // =================================

        System.out.println("========== MINIMUM DP ==========");

        System.out.println("1D:");
        System.out.println(Arrays.toString(min1D));

        System.out.println("2D:");
        for (int[] row : min2D) {
            System.out.println(Arrays.toString(row));
        }

        System.out.println("3D:");
        for (int[][] matrix : min3D) {
            for (int[] row : matrix) {
                System.out.println(Arrays.toString(row));
            }
            System.out.println();
        }

        System.out.println("========== MAXIMUM DP ==========");

        System.out.println("1D:");
        System.out.println(Arrays.toString(max1D));

        System.out.println("2D:");
        for (int[] row : max2D) {
            System.out.println(Arrays.toString(row));
        }

        System.out.println("3D:");
        for (int[][] matrix : max3D) {
            for (int[] row : matrix) {
                System.out.println(Arrays.toString(row));
            }
            System.out.println();
        }

        System.out.println("========== COUNTING DP ==========");

        System.out.println("1D:");
        System.out.println(Arrays.toString(count1D));

        System.out.println("2D:");
        for (int[] row : count2D) {
            System.out.println(Arrays.toString(row));
        }

        System.out.println("3D:");
        for (int[][] matrix : count3D) {
            for (int[] row : matrix) {
                System.out.println(Arrays.toString(row));
            }
            System.out.println();
        }

        System.out.println("========== BOOLEAN DP ==========");

        System.out.println("1D:");
        System.out.println(Arrays.toString(bool1D));

        System.out.println("2D:");
        for (boolean[] row : bool2D) {
            System.out.println(Arrays.toString(row));
        }

        System.out.println("3D:");
        for (boolean[][] matrix : bool3D) {
            for (boolean[] row : matrix) {
                System.out.println(Arrays.toString(row));
            }
            System.out.println();
        }
    }
}
```
## Expected output

```text
========== MINIMUM DP ==========
1D:
[0, 2147483647, 2147483647, 2147483647, 2147483647]
2D:
[0, 2147483647, 2147483647, 2147483647]
[2147483647, 2147483647, 2147483647, 2147483647]
[2147483647, 2147483647, 2147483647, 2147483647]
[2147483647, 2147483647, 2147483647, 2147483647]
[2147483647, 2147483647, 2147483647, 2147483647]
3D:
[0, 2147483647, 2147483647]
[2147483647, 2147483647, 2147483647]
[2147483647, 2147483647, 2147483647]
[2147483647, 2147483647, 2147483647]

[2147483647, 2147483647, 2147483647]
[2147483647, 2147483647, 2147483647]
[2147483647, 2147483647, 2147483647]
[2147483647, 2147483647, 2147483647]

[2147483647, 2147483647, 2147483647]
[2147483647, 2147483647, 2147483647]
[2147483647, 2147483647, 2147483647]
[2147483647, 2147483647, 2147483647]

[2147483647, 2147483647, 2147483647]
[2147483647, 2147483647, 2147483647]
[2147483647, 2147483647, 2147483647]
[2147483647, 2147483647, 2147483647]

[2147483647, 2147483647, 2147483647]
[2147483647, 2147483647, 2147483647]
[2147483647, 2147483647, 2147483647]
[2147483647, 2147483647, 2147483647]

========== MAXIMUM DP ==========
1D:
[0, -2147483648, -2147483648, -2147483648, -2147483648]
2D:
[0, -2147483648, -2147483648, -2147483648]
[-2147483648, -2147483648, -2147483648, -2147483648]
[-2147483648, -2147483648, -2147483648, -2147483648]
[-2147483648, -2147483648, -2147483648, -2147483648]
[-2147483648, -2147483648, -2147483648, -2147483648]
3D:
[0, -2147483648, -2147483648]
[-2147483648, -2147483648, -2147483648]
[-2147483648, -2147483648, -2147483648]
[-2147483648, -2147483648, -2147483648]

[-2147483648, -2147483648, -2147483648]
[-2147483648, -2147483648, -2147483648]
[-2147483648, -2147483648, -2147483648]
[-2147483648, -2147483648, -2147483648]

[-2147483648, -2147483648, -2147483648]
[-2147483648, -2147483648, -2147483648]
[-2147483648, -2147483648, -2147483648]
[-2147483648, -2147483648, -2147483648]

[-2147483648, -2147483648, -2147483648]
[-2147483648, -2147483648, -2147483648]
[-2147483648, -2147483648, -2147483648]
[-2147483648, -2147483648, -2147483648]

[-2147483648, -2147483648, -2147483648]
[-2147483648, -2147483648, -2147483648]
[-2147483648, -2147483648, -2147483648]
[-2147483648, -2147483648, -2147483648]

========== COUNTING DP ==========
1D:
[1, 0, 0, 0, 0]
2D:
[1, 0, 0, 0]
[0, 0, 0, 0]
[0, 0, 0, 0]
[0, 0, 0, 0]
[0, 0, 0, 0]
3D:
[1, 0, 0]
[0, 0, 0]
[0, 0, 0]
[0, 0, 0]

[0, 0, 0]
[0, 0, 0]
[0, 0, 0]
[0, 0, 0]

[0, 0, 0]
[0, 0, 0]
[0, 0, 0]
[0, 0, 0]

[0, 0, 0]
[0, 0, 0]
[0, 0, 0]
[0, 0, 0]

[0, 0, 0]
[0, 0, 0]
[0, 0, 0]
[0, 0, 0]

========== BOOLEAN DP ==========
1D:
[true, false, false, false, false]
2D:
[true, false, false, false]
[false, false, false, false]
[false, false, false, false]
[false, false, false, false]
[false, false, false, false]
3D:
[true, false, false]
[false, false, false]
[false, false, false]
[false, false, false]

[false, false, false]
[false, false, false]
[false, false, false]
[false, false, false]

[false, false, false]
[false, false, false]
[false, false, false]
[false, false, false]

[false, false, false]
[false, false, false]
[false, false, false]
[false, false, false]

[false, false, false]
[false, false, false]
[false, false, false]
[false, false, false]


```
## Important: How to print different dimensions

| Array | Printing method |
| --- | --- |
| 1D | `Arrays.toString(arr)` |
| 2D | `Arrays.toString(row)` inside a loop |
| 3D | Nested loops + `Arrays.toString(row)` |

One thing to remember: In 3D printing, each `matrix` represents one 2D layer, and each `row` represents one 1D array.
