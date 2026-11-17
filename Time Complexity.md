# Time Complexity : Complete Study Guide

**Time complexity** describes how the amount of computer time required to run an algorithm scales as the size of the input ($n$) grows. Instead of measuring raw execution time in seconds—which depends heavily on the machine, compiler, or processor load—it counts the number of elementary operations or statement executions.

---

## 1. Big O Notation
Time complexity is typically expressed using **Big O notation** ($O$), which focuses on the asymptotic upper bound—the dominant term that dictates growth for large inputs while dropping constant factors and lower-order terms.

---

## 2. Time Complexities in Ascending Order (Fastest to Slowest)

| Order | Complexity | Name | Growth Behavior & Example |
| :--- | :--- | :--- | :--- |
| **1** | **$O(1)$** | Constant | Execution time stays the same regardless of input size. Example: Accessing an array element by index. |
| **2** | **$O(\log n)$** | Logarithmic | Execution time grows very slowly as input doubles. Example: Binary search. |
| **3** | **$O(\sqrt{n})$** | Square Root | Execution time scales with the square root of the input. Example: Checking if a number is prime. |
| **4** | **$O(n)$** | Linear | Execution time grows directly in proportion to input size. Example: Looping through an array once. |
| **5** | **$O(n \log n)$** | Linearithmic | Execution time combines linear and logarithmic growth. Example: Merge Sort and Heap Sort. |
| **6** | **$O(n^2)$** | Quadratic | Execution time grows proportionally to the square of the input. Example: Nested loops in Bubble Sort. |
| **7** | **$O(n^3)$** | Cubic | Execution time grows proportionally to the cube of the input. Example: Triple nested loops. |
| **8** | **$O(2^n)$** | Exponential | Execution time doubles with each single addition to the input. Example: Solving the Traveling Salesperson Problem via brute force. |
| **9** | **$O(n!)$** | Factorial | Execution time multiplies by the input size for every new element. Example: Generating all permutations of a string. |

---

## 3. How to Identify Time Complexity in Code

Look at how many times your code repeats operations as the input size ($n$) grows:

* **$O(1)$ — Constant:** Look for simple math, variable assignments, or direct array/hash map lookups without loops. The code runs in the exact same number of steps no matter how big $n$ gets.
* **$O(\log n)$ — Logarithmic:** Look for loops where the loop variable is multiplied or divided by a constant in each step (such as `i = i * 2` or `n = n / 2`). This pattern means you cut the problem size in half every time.
* **$O(n)$ — Linear:** Look for a single loop that visits every element from `0` to `n`. Two separate loops placed one after another still equal $O(n)$ because you drop constant multipliers like $2n$.
* **$O(n \log n)$ — Linearithmic:** Look for a standard $O(n)$ loop that contains a logarithmic operation inside it. This also appears when you sort a list first or use divide-and-conquer algorithms like Merge Sort.
* **$O(n^2)$ — Quadratic:** Look for nested loops where both the outer and inner loops run up to $n$. Checking every possible pair of elements in a list usually creates this pattern.
* **$O(2^n)$ — Exponential:** Look for recursive functions that branch into two or more new calls on every step without saving past results.

---

## 4. What to Use When in Code (By Input Size)

In coding interviews and competitive programming, your maximum input size ($n$) tells you which complexity will run fast enough (typically under 1 second, or about $10^8$ operations).

| Input Size ($n$) | Target Complexity | What to Use in Code |
| :--- | :--- | :--- |
| **$n \le 10$** | **$O(n!)$** or **$O(2^n)$** | Backtracking, brute-force recursion, or generating all permutations. |
| **$n \le 20$** | **$O(2^n)$** | Recursion with bitmasking or exploring all subsets. |
| **$n \le 500$** | **$O(n^3)$** | Triple nested loops or basic dynamic programming on 2D grids. |
| **$n \le 5,000$** | **$O(n^2)$** | Double nested loops, comparing all pairs, or simple sorting like Insertion Sort. |
| **$n \le 10^6$** | **$O(n \log n)$** or **$O(n)$** | Built-in sorting (`sort()`), two pointers, sliding window, or hash maps. |
| **$n > 10^6$** | **$O(\log n)$** or **$O(1)$** | Binary search, mathematical formulas, or bit manipulation. |

### Quick Optimization Tips
* **Trade space for speed:** Use a Hash Map or Set to turn slow $O(n^2)$ nested searches into fast $O(n)$ lookups.
* **Sort first:** If your data is unsorted and requires repeated searching, sorting it once in $O(n \log n)$ lets you use fast $O(\log n)$ binary search afterward.

---

## 5. Conclusion & Key Takeaways

**Mastering time complexity** comes down to writing code that scales smoothly as data grows rather than slowing down or crashing on large inputs. By counting how loops and recursive calls repeat, you can quickly judge efficiency and pick the right data structures before writing a single line of code.

* **Focus on growth, not seconds:** Time complexity measures how the number of steps increases with input size ($n$), making it independent of computer hardware.
* **Drop constants and small terms:** Always simplify to the slowest-growing dominant part, such as turning $2n + 5$ into $O(n)$ or $n^2 + n$ into $O(n^2)$.
* **Spot the code structure:** Single loops usually mean $O(n)$, nested loops mean $O(n^2)$, and halving the search space on each step means $O(\log n)$.
* **Let input size guide your choice:** Small inputs allow simple brute force, while large inputs ($n \ge 10^5$) demand fast $O(n \log n)$, $O(n)$, or $O(\log n)$ solutions.
* **Balance time and memory:** Using extra memory with tools like hash maps or caching often turns slow quadratic code into fast linear code.
