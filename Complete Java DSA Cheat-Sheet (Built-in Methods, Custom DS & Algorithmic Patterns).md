# Complete Java DSA Cheat-Sheet (Built-in + Custom DS & Algorithms)

---

## 1. Sorting & Searching Algorithms (`Arrays` & `Collections`)

| Task | Array (`int[]` / `T[]`) | List (`List<T>`) | Complexity & Note |
| :--- | :--- | :--- | :--- |
| **Ascending Sort** | `Arrays.sort(arr)` | `Collections.sort(list)` | `O(n log n)` |
| **Partial Sort (Range)** | `Arrays.sort(arr, fromIdx, toIdx)` | *(Not direct)* | `toIdx` exclusive hota hai |
| **Descending Sort** | `Arrays.sort(arr, Collections.reverseOrder())` | `Collections.sort(list, Collections.reverseOrder())` | `arr` primitive (`int[]`) nahi, `Integer[]` hona chahiye |
| **Custom Sort (Comparator)** | `Arrays.sort(arr, (a, b) -> a - b)` | `Collections.sort(list, (a, b) -> a - b)` | 2D arrays ya custom objects sort karne ke liye |
| **Parallel Sort** | `Arrays.parallelSort(arr)` | *(Not direct)* | Bahut bade arrays (`> 10^5`) ke liye fast |
| **Binary Search** | `Arrays.binarySearch(arr, key)` | `Collections.binarySearch(list, key)` | `O(log n)` — Array/List pehle se **sorted** honi chahiye |
| **Range Binary Search** | `Arrays.binarySearch(arr, fromIdx, toIdx, key)` | *(Not direct)* | Agar key na mile toh `-(insertionPoint) - 1` return hota hai |

---

## 2. Array & Collection Manipulation Utilities

### A. `java.util.Arrays` Methods
* `Arrays.fill(arr, val)` — Poore array mein ek hi default value (`0`, `-1`, `true`) bharna.
* `Arrays.fill(arr, fromIdx, toIdx, val)` — Specific range mein value bharna.
* `Arrays.copyOf(arr, newLength)` — Array ki copy banana (size badha ya ghata bhi sakte hain).
* `Arrays.copyOfRange(arr, fromIdx, toIdx)` — Array ka ek subarray slice nikalna.
* `Arrays.equals(arr1, arr2)` — Do 1D arrays ke elements equal hain ya nahi (`true/false`).
* `Arrays.deepEquals(mat1, mat2)` — Do 2D/3D arrays ko compare karne ke liye.
* `Arrays.toString(arr)` — Debugging ke liye 1D array ko readable string mein print karna.
* `Arrays.deepToString(mat)` — 2D/3D matrix ko print karna.
* `Arrays.mismatch(arr1, arr2)` — Pehla index return karta hai jahan do arrays alag hain (`-1` agar same hain).
* `Arrays.asList(arr)` — Array ko fixed-size `List` mein badalna.

### B. `java.util.Collections` Methods
* `Collections.reverse(list)` — List ko in-place ulta (`O(n)`) karna.
* `Collections.max(list)` / `Collections.min(list)` — Sabse bada / sabse chota element nikalna (`O(n)`).
* `Collections.swap(list, i, j)` — Index `i` aur `j` ke elements ko aapas mein badalna (`O(1)`).
* `Collections.frequency(list, target)` — `target` list mein kitni baar aaya hai (`O(n)`).
* `Collections.rotate(list, distance)` — List ko `distance` steps right rotate karna (negative distance se left rotate).
* `Collections.shuffle(list)` — Elements ko randomly shuffle karna.
* `Collections.fill(list, val)` — Poore list mein ek value bharna.
* `Collections.nCopies(n, val)` — `n` size ki list banana jisme har jagah `val` ho.
* `Collections.disjoint(list1, list2)` — Check karta hai ki kya dono lists mein **koi bhi common element nahi** hai (`true/false`).
* `Collections.replaceAll(list, oldVal, newVal)` — Sabhi `oldVal` ko `newVal` se replace karna.

---

## 3. Math & Number Algorithms (`java.lang.Math`)
* `Math.max(a, b)` / `Math.min(a, b)` — Do numbers mein bada ya chota.
* `Math.abs(a)` — Negative number ko positive banana (`|-5| = 5`).
* `Math.pow(base, exp)` — Power nikalna (`double` return karta hai).
* `Math.sqrt(n)` / `Math.cbrt(n)` — Square root aur Cube root.
* `Math.ceil(x)` / `Math.floor(x)` / `Math.round(x)` — Rounding functions.
* `Math.log(x)` / `Math.log10(x)` — Natural log aur Base-10 log (digits count karne ke liye: `(int)Math.log10(n) + 1`).

---

## 4. Complete Bit Manipulation (`Integer` / `Long` & Operators)

### A. Bitwise Operators
* `&` **(Bitwise AND):** Dono bits `1` hon toh `1` (Even/Odd check: `(n & 1) == 0`).
* `|` **(Bitwise OR):** Koi ek bit `1` ho toh `1` (Kisi bit ko set/ON karne ke liye: `n | (1 << k)`).
* `^` **(Bitwise XOR):** Dono bits alag hon toh `1` (Duplicate hatane ya swap karne ke liye: `a ^ a = 0`).
* `~` **(Bitwise NOT):** Saare bits flip karta hai (`0` ko `1` aur `1` ko `0`).
* `<<` **(Left Shift):** Bits ko left khiskata hai (`n << k` ka matlab `n * 2^k`).
* `>>` **(Arithmetic Right Shift):** Sign bit ko bachate hue right khiskata hai (`n >> k` ka matlab `n / 2^k`).
* `>>>` **(Unsigned Right Shift):** Left mein hamesha `0` bharta hai (negative numbers ke liye useful).

### B. `Integer` (aur `Long`) ke Built-in Bit Methods
*(Sabhi methods `Long.bitCount(n)` ke roop mein `long` ke liye bhi available hain)*:
* `Integer.bitCount(n)` — Binary representation mein total **`1`s (set bits)** ginta hai.
* `Integer.highestOneBit(n)` — Sabse left wale `1` bit ki value deta hai (e.g., `10` (`1010`) → `8` (`1000`)).
* `Integer.lowestOneBit(n)` — Sabse right wale `1` bit ki value deta hai (e.g., `10` (`1010`) → `2` (`0010`)).
* `Integer.numberOfLeadingZeros(n)` — 32-bit integer mein pehle `1` se pehle kitne `0` hain.
* `Integer.numberOfTrailingZeros(n)` — Sabse aakhri `1` ke baad kitne `0` hain.
* `Integer.reverse(n)` — Poore 32 bits ka order ulta kar deta hai.
* `Integer.reverseBytes(n)` — Bytes ka order ulta karta hai.
* `Integer.rotateLeft(n, dist)` / `Integer.rotateRight(n, dist)` — Bits ko circular rotate karta hai.
* `Integer.toBinaryString(n)` — Integer ko binary `String` (`"1010"`) mein badalta hai.
* `Integer.parseInt("1010", 2)` — Binary string ko wapas integer (`10`) mein badalta hai.

---

## 5. Custom Data Structures (Jo Khud Likhne Padte Hain)

| Data Structure | Java Blueprint / Structure | Key Operations & Complexity | Main Use Cases |
| :--- | :--- | :--- | :--- |
| **Singly / Doubly LinkedList** | `class ListNode { int val; ListNode next, prev; }` | Insert/Delete at head: `O(1)`, Search: `O(n)` | Cycle detection (Floyd's), Reverse list, Merge sorted lists, LRU Cache |
| **Binary Tree & BST** | `class TreeNode { int val; TreeNode left, right; }` | BST Search/Insert: `O(log n)` avg, Traversals: `O(n)` | Hierarchical data, LCA, Height/Diameter, Inorder/Preorder/Postorder |
| **Graph (Adjacency List)** | `List<List<Integer>> adj = new ArrayList<>();` *(Weighted ke liye `List<int[]>`)* | Add edge: `O(1)`, Traversal: `O(V + E)` | Networks, Maps, Connected components, Shortest paths |
| **Trie (Prefix Tree)** | `class TrieNode { TrieNode[] children = new TrieNode[26]; boolean isEnd; }` | Insert/Search prefix: `O(L)` *(L = word length)* | Autocomplete, Spell checker, Word search in grid |
| **Disjoint Set (Union-Find)** | `int[] parent, rank;` with `find(x)` & `union(x, y)` | Path compression + Union by rank: `O(α(n)) ≈ O(1)` | Dynamic connectivity, Cycle detection in undirected graph, Kruskal's MST |
| **Segment Tree / Fenwick Tree** | `int[] tree = new int[4 * n];` | Build: `O(n)`, Range Query & Point Update: `O(log n)` | Range Sum/Min/Max queries with frequent array updates |

---

## 6. Core Algorithmic Patterns & Techniques

### A. Linear & Array Patterns
* **Two Pointers:** Ek ya do arrays par do indices (`left`, `right` ya `slow`, `fast`) move karna (`O(n)`).
  * *Examples:* Two Sum (sorted), Container With Most Water, Remove Duplicates, Fast & Slow pointer cycle check.
* **Sliding Window:** Fixed ya variable size ki window `[left...right]` maintain karna (`O(n)`).
  * *Examples:* Max sum subarray of size K, Longest substring without repeating characters.
* **Prefix Sum & Difference Array:** Cumulative sums store karke range sum queries ko `O(1)` mein solve karna.
  * *Examples:* Subarray sum equals K, Range addition queries.

### B. Search, Recursion & Optimization Patterns
* **Modified Binary Search:** Sorted array ke alawa **Binary Search on Answer** (monotonic search space) par lagana (`O(log n)`).
  * *Examples:* Search in Rotated Sorted Array, Koko Eating Bananas, Allocate Minimum Pages.
* **Recursion & Backtracking:** Saare possible combinations explore karna aur invalid paths se wapas lautna (`O(2^n)` ya `O(n!)`).
  * *Examples:* Subsets, Permutations, Combination Sum, N-Queens, Sudoku Solver.
* **Greedy Algorithms:** Har step par local best choice lena taaki global optimum mile (`O(n log n)` mostly sorting ke saath).
  * *Examples:* Activity Selection / Merge Intervals, Fractional Knapsack, Jump Game, Huffman Coding.
* **Dynamic Programming (DP):** Overlapping subproblems ke results ko save karke exponential time ko polynomial mein badalna.
  * **Memoization (Top-Down):** Recursion + `dp[]` / `HashMap` cache.
  * **Tabulation (Bottom-Up):** Iterative loops + `dp[]` / `dp[][]` table.
  * *Classic DP Patterns:* 0/1 Knapsack, Unbounded Knapsack, Longest Common Subsequence (LCS), Longest Increasing Subsequence (LIS), Grid Paths, DP on Trees.

### C. Graph Algorithms
* **BFS (Breadth-First Search):** `Queue` ka use karke level-by-level traversal; **unweighted graph mein shortest path** deta hai (`O(V + E)`).
* **DFS (Depth-First Search):** Recursion ya `Stack` se depth mein jaana; cycle detection, connected components, aur path finding (`O(V + E)`).
* **Dijkstra's Algorithm:** `PriorityQueue` (Min-Heap) ka use karke **non-negative weighted graph mein single-source shortest path** (`O(E log V)`).
* **Bellman-Ford & Floyd-Warshall:** Negative edge weights handle karne (`O(V * E)`) aur All-Pairs Shortest Path (`O(V^3)`) ke liye.
* **Topological Sort (Kahn's Algorithm / DFS):** Directed Acyclic Graph (DAG) mein dependencies ka linear order nikalne ke liye (`O(V + E)`).
* **Minimum Spanning Tree (Kruskal's & Prim's):** Poore graph ko minimum total edge weight se connect karne ke liye (`O(E log E)`).
