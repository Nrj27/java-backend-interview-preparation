# Space Complexity: Complete Study Guide

**Space complexity** is the total amount of memory an algorithm or data structure needs to run to completion, measured as a function of the input size (`n`). Expressed using **Big O notation**, it describes how memory usage scales as input data grows.

---

## 1. Key Components
Total space complexity consists of two parts:
* **Auxiliary Space:** The extra or temporary memory allocated during execution (variables, temporary arrays, hash maps, and the recursive call stack). Engineers focus primarily on this metric when comparing algorithms.
* **Input Space:** The memory required to hold the original input data itself, which remains fixed regardless of the algorithm chosen.

---

## 2. Ascending Order of Complexity (Best to Worst)
From most memory-efficient to most memory-intensive:

`O(1) < O(log n) < O(√n) < O(n) < O(n log n) < O(n²) < O(n³) < O(2ⁿ) < O(n!)`

* **O(1) — Constant:** Memory stays fixed regardless of input size.
* **O(log n) — Logarithmic:** Memory grows very slowly as input increases.
* **O(√n) — Square Root:** Memory grows proportionally to the square root of the input.
* **O(n) — Linear:** Memory grows directly in proportion to the input size.
* **O(n log n) — Linearithmic:** Slightly more memory than linear (e.g., certain non-in-place sorting buffers).
* **O(n²) — Quadratic:** Memory grows with the square of the input size.
* **O(n³) — Cubic:** Memory grows with the cube of the input size.
* **O(2ⁿ) — Exponential:** Memory doubles with every single addition to the input.
* **O(n!) — Factorial:** Memory grows at an extreme rate, exhausting RAM even on tiny inputs.

---

## 3. How to Identify Space Complexity in Code
Check for **new memory allocations** and **recursive call stacks** that scale with `n`:

* **O(1) — Constant Space:**
  * Look for single variables, loop counters, or pointers (`int sum = 0`, `left = 0`).
  * Modifying the input array directly (in-place) without creating new collections.
* **O(log n) — Logarithmic Space:**
  * Look for divide-and-conquer recursion where the problem size is divided by a constant factor on every step (e.g., `binarySearch(arr, mid + 1, high)`).
* **O(n) — Linear Space:**
  * Look for new 1D arrays, lists, hash maps, or sets whose size matches the input (`new int[n]`, `seen = set()`).
  * Single-branch recursion that runs `n` layers deep (e.g., `factorial(n - 1)`).
* **O(n²) — Quadratic Space:**
  * Look for nested 2D structures (`new int[n][n]`), graph adjacency matrices, or lists storing all possible pairs of elements.

---

## 4. What to Use and When (Decision Guide)

| Target Space | When to Use It | Common Techniques |
| :--- | :--- | :--- |
| **O(1)** | Massive datasets or strict RAM limits (mobile apps, embedded systems, microcontrollers). | **Two-pointer technique**, sliding window, or sorting/modifying data in-place. |
| **O(log n)** | Solving divide-and-conquer problems cleanly without duplicating data. | **Recursive binary search** or balanced binary tree traversals. |
| **O(n)** | Speeding up slow nested loops by trading extra RAM to drop runtime from `O(n²)` to `O(n)`. | **Hash maps/sets** for instant lookups, queues for BFS, or 1D dynamic programming arrays. |
| **O(n²)** | Complex optimization problems where two variables change simultaneously and results must be cached. | **2D dynamic programming tables** (e.g., grid paths, edit distance) or adjacency matrices. |

---

## 5. Final Takeaways
* **Focus on Growth, Not Exact Bytes:** Ignore fixed overhead like single variables; focus only on data structures and call stacks that expand as `n` grows.
* **Master the Time-Space Trade-Off:** Modern hardware usually has plenty of RAM. Trading **O(n)** extra space (such as a hash map) to reduce a slow **O(n²)** runtime down to **O(n)** is almost always worthwhile.
* **Respect Hardware Constraints:** Prioritize **O(1)** in-place techniques when working with memory-constrained environments to prevent Out-Of-Memory crashes.
* **Keep a Practical Ceiling:** Aim for **O(1)**, **O(log n)**, or **O(n)** in production code. Treat **O(n²)** or higher as a red flag unless you are certain `n` will remain small (typically under 10,000 items).
