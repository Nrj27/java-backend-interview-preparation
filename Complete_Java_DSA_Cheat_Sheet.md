# Complete Java DSA Cheat-Sheet (Built-in Methods, Custom DS & Algorithmic Patterns)

---

## 1. Built-in Linear & Associative Data Structures (`java.util.*`)

| Data Structure | Java Class | Initialization | Sabse Zaroori Methods & Complexity |
| :--- | :--- | :--- | :--- |
| **Dynamic Array** | `ArrayList` | `List<Integer> list = new ArrayList<>();` *(Fixed size `n`: `new ArrayList<>(Collections.nCopies(n, 0))`)* | `add(val)` (`O(1)`), `get(idx)` (`O(1)`), `set(idx, val)` (`O(1)`), `remove(idx)` (`O(n)`), `size()`, `contains(val)` |
| **Fast String** | `StringBuilder` | `StringBuilder sb = new StringBuilder();` | `append(str)` (`O(1)`), `insert(idx, str)`, `deleteCharAt(idx)`, `reverse()` (`O(n)`), `toString()` |
| **Stack (LIFO)** | `ArrayDeque` | `Deque<Integer> st = new ArrayDeque<>();` | `push(val)` (`O(1)`), `pop()` (`O(1)`), `peek()` (`O(1)`), `isEmpty()` |
| **Queue (FIFO)** | `LinkedList` / `ArrayDeque` | `Queue<Integer> q = new LinkedList<>();` | `offer(val)` (`O(1)`), `poll()` (`O(1)`), `peek()` (`O(1)`), `isEmpty()` |
| **Deque (2-Way)** | `ArrayDeque` | `Deque<Integer> dq = new ArrayDeque<>();` | `offerFirst()`, `offerLast()`, `pollFirst()`, `pollLast()`, `peekFirst()`, `peekLast()` (`O(1)`) |
| **Min / Max Heap** | `PriorityQueue` | **Min:** `new PriorityQueue<>()`<br>**Max:** `new PriorityQueue<>(Collections.reverseOrder())` | `offer(val)` (`O(log n)`), `poll()` (`O(log n)`), `peek()` (`O(1)`) |
| **Hash Map** | `HashMap` | `Map<Integer, Integer> map = new HashMap<>();` | `put(k, v)` (`O(1)`), `get(k)` (`O(1)`), `getOrDefault(k, 0)`, `containsKey(k)`, `remove(k)`, `keySet()` |
| **Hash Set** | `HashSet` | `Set<Integer> set = new HashSet<>();` | `add(val)` (`O(1)`), `contains(val)` (`O(1)`), `remove(val)` (`O(1)`), `size()` |
| **Sorted Set / Map** | `TreeSet` / `TreeMap` | `TreeSet<Integer> ts = new TreeSet<>();` | `first()`, `last()`, `floor(x)`, `ceiling(x)`, `lower(x)`, `higher(x)` (`O(log n)`) |
| **Doubly LinkedList** | `LinkedList` | `LinkedList<Integer> ll = new LinkedList<>();` | `addFirst()`, `addLast()`, `removeFirst()`, `removeLast()`, `getFirst()`, `getLast()` (`O(1)`) |

### Code Example: Built-in Data Structures
```java
// Frequency Map using getOrDefault
Map<Integer, Integer> freq = new HashMap<>();
for (int x : arr) {
    freq.put(x, freq.getOrDefault(x, 0) + 1);
}

// Max-Heap
PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());
maxHeap.offer(10);
maxHeap.offer(30);
int largest = maxHeap.poll(); // 30
```

---

## 2. Sorting & Searching Algorithms (`Arrays` & `Collections`)

| Task | Array (`int[]` / `T[]`) | List (`List<T>`) | Complexity & Note |
| :--- | :--- | :--- | :--- |
| **Ascending Sort** | `Arrays.sort(arr)` | `Collections.sort(list)` | `O(n log n)` |
| **Partial Sort (Range)** | `Arrays.sort(arr, fromIdx, toIdx)` | *(Not direct)* | `toIdx` exclusive hota hai |
| **Descending Sort** | `Arrays.sort(arr, Collections.reverseOrder())` | `Collections.sort(list, Collections.reverseOrder())` | `arr` primitive (`int[]`) nahi, `Integer[]` hona chahiye |
| **Custom Sort (Comparator)** | `Arrays.sort(arr, (a, b) -> a[0] - b[0])` | `Collections.sort(list, (a, b) -> a[0] - b[0])` | 2D arrays ya custom objects sort karne ke liye |
| **Parallel Sort** | `Arrays.parallelSort(arr)` | *(Not direct)* | Bahut bade arrays (`> 10^5`) ke liye fast |
| **Binary Search** | `Arrays.binarySearch(arr, key)` | `Collections.binarySearch(list, key)` | `O(log n)` — Array/List pehle se **sorted** honi chahiye |
| **Range Binary Search** | `Arrays.binarySearch(arr, fromIdx, toIdx, key)` | *(Not direct)* | Agar key na mile toh `-(insertionPoint) - 1` return hota hai |

### Code Example: Sorting & Binary Search
```java
int[] arr = {5, 2, 9, 1};
Arrays.sort(arr); // [1, 2, 5, 9]
int idx = Arrays.binarySearch(arr, 5); // Output: 2

// 2D Array sort by 2nd column (index 1)
int[][] intervals = {{1, 4}, {2, 3}, {0, 5}};
Arrays.sort(intervals, (a, b) -> Integer.compare(a[1], b[1]));
```

---

## 3. Array, Collection & Math Utilities

### A. `java.util.Arrays` Methods
* `Arrays.fill(arr, val)` / `Arrays.fill(arr, fromIdx, toIdx, val)` — Default value bharna.
* `Arrays.copyOf(arr, newLength)` / `Arrays.copyOfRange(arr, fromIdx, toIdx)` — Array copy/slice karna.
* `Arrays.equals(arr1, arr2)` / `Arrays.deepEquals(mat1, mat2)` — 1D aur 2D arrays compare karna.
* `Arrays.toString(arr)` / `Arrays.deepToString(mat)` — Debugging ke liye array/matrix print karna.
* `Arrays.mismatch(arr1, arr2)` — Pehla index jahan arrays alag hain (`-1` agar same hain).
* `Arrays.asList(arr)` — Array ko fixed-size `List` mein badalna.

### B. `java.util.Collections` Methods
* `Collections.reverse(list)` — List ko in-place ulta (`O(n)`) karna.
* `Collections.max(list)` / `Collections.min(list)` — Max / Min element (`O(n)`).
* `Collections.swap(list, i, j)` — Elements swap karna (`O(1)`).
* `Collections.frequency(list, target)` — `target` kitni baar aaya hai (`O(n)`).
* `Collections.rotate(list, distance)` — List ko rotate karna.
* `Collections.shuffle(list)` — Elements ko randomly shuffle karna.
* `Collections.nCopies(n, val)` — `n` size ki list `val` ke saath banana.
* `Collections.disjoint(list1, list2)` — Kya dono lists mein koi common element nahi hai (`true/false`).
* `Collections.replaceAll(list, oldVal, newVal)` — Sabhi `oldVal` ko `newVal` se replace karna.

### C. `java.lang.Math` Methods
* `Math.max(a, b)` / `Math.min(a, b)` — Bada ya chota number.
* `Math.abs(a)` — Absolute value (`|-5| = 5`).
* `Math.pow(base, exp)` / `Math.sqrt(n)` / `Math.cbrt(n)` — Power aur roots.
* `Math.ceil(x)` / `Math.floor(x)` / `Math.round(x)` — Rounding functions.
* `Math.log(x)` / `Math.log10(n)` — Natural log & Base-10 log (digits count: `(int) Math.log10(n) + 1`).

### Code Example: Utilities
```java
int[] dp = new int[5];
Arrays.fill(dp, -1); // [-1, -1, -1, -1, -1]

List<Integer> list = new ArrayList<>(Arrays.asList(10, 20, 30, 20));
int count = Collections.frequency(list, 20); // 2
Collections.reverse(list); // [20, 30, 20, 10]
```

---

## 4. Complete Bit Manipulation (`Integer` / `Long` & Operators)

### A. Bitwise Operators & Common Tricks
* `&` **(Bitwise AND):** Even/Odd check → `(n & 1) == 0` (Even)
* `|` **(Bitwise OR):** `k`-th bit ON (set) karna → `n | (1 << k)`
* `^` **(Bitwise XOR):** Duplicate hatana (`a ^ a = 0`), `k`-th bit toggle karna → `n ^ (1 << k)`
* `~` **(Bitwise NOT):** `k`-th bit OFF (clear) karna → `n & ~(1 << k)`
* `<<` **(Left Shift):** `n << k` = `n * 2^k`
* `>>` **(Arithmetic Right Shift):** `n >> k` = `n / 2^k`
* `>>>` **(Unsigned Right Shift):** Left mein hamesha `0` bharta hai.

### B. `Integer` (aur `Long`) Built-in Bit Methods
*(Sabhi methods `Long.bitCount(n)` ke roop mein `long` ke liye bhi available hain)*:
* `Integer.bitCount(n)` — Binary representation mein total **`1`s (set bits)** ginta hai.
* `Integer.highestOneBit(n)` / `Integer.lowestOneBit(n)` — Leftmost / Rightmost set bit ki value.
* `Integer.numberOfLeadingZeros(n)` / `Integer.numberOfTrailingZeros(n)` — Leading / Trailing `0` bits.
* `Integer.reverse(n)` / `Integer.reverseBytes(n)` — Bits / Bytes ka order ulta karna.
* `Integer.rotateLeft(n, dist)` / `Integer.rotateRight(n, dist)` — Circular bit rotation.
* `Integer.toBinaryString(n)` / `Integer.parseInt("1010", 2)` — Binary String conversion.

### Code Example: Bit Manipulation
```java
int n = 10; // Binary: 1010
int setBits = Integer.bitCount(n); // 2
boolean isPowerOfTwo = (n > 0) && ((n & (n - 1)) == 0); // false
int k = 0;
int afterSetting0thBit = n | (1 << k); // 11 (Binary: 1011)
```

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

### Code Blueprints: Custom Data Structures

#### A. LinkedList & Binary Tree Nodes
```java
class ListNode {
    int val;
    ListNode next;
    ListNode(int val) { this.val = val; }
}

class TreeNode {
    int val;
    TreeNode left, right;
    TreeNode(int val) { this.val = val; }
}
```

#### B. Trie (Prefix Tree)
```java
class TrieNode {
    TrieNode[] children = new TrieNode[26];
    boolean isEnd = false;
}

class Trie {
    TrieNode root = new TrieNode();
    
    public void insert(String word) {
        TrieNode curr = root;
        for (char c : word.toCharArray()) {
            if (curr.children[c - 'a'] == null) {
                curr.children[c - 'a'] = new TrieNode();
            }
            curr = curr.children[c - 'a'];
        }
        curr.isEnd = true;
    }
    
    public boolean search(String word) {
        TrieNode curr = root;
        for (char c : word.toCharArray()) {
            if (curr.children[c - 'a'] == null) return false;
            curr = curr.children[c - 'a'];
        }
        return curr.isEnd;
    }
}
```

#### C. Disjoint Set (Union-Find with Path Compression)
```java
class DSU {
    int[] parent, rank;
    
    DSU(int n) {
        parent = new int[n];
        rank = new int[n];
        for (int i = 0; i < n; i++) parent[i] = i;
    }
    
    int find(int x) {
        if (parent[x] != x) parent[x] = find(parent[x]); // Path compression
        return parent[x];
    }
    
    boolean union(int x, int y) {
        int px = find(x), py = find(y);
        if (px == py) return false; // Already connected (cycle)
        if (rank[px] < rank[py]) parent[px] = py;
        else if (rank[px] > rank[py]) parent[py] = px;
        else { parent[py] = px; rank[px]++; }
        return true;
    }
}
```

---

## 6. Core Algorithmic Patterns & Code Templates

### A. Linear & Array Patterns
* **Two Pointers:** Ek ya do arrays par do indices (`left`, `right` ya `slow`, `fast`) move karna (`O(n)`).
  * *Examples:* Two Sum (sorted), Container With Most Water, Remove Duplicates, Fast & Slow pointer cycle check.
* **Sliding Window:** Fixed ya variable size ki window `[left...right]` maintain karna (`O(n)`).
  * *Examples:* Max sum subarray of size K, Longest substring without repeating characters.
* **Prefix Sum & Difference Array:** Cumulative sums store karke range sum queries ko `O(1)` mein solve karna.
  * *Examples:* Subarray sum equals K, Range addition queries.

```java
// 1. Two Pointers Example (Sorted Two-Sum)
int[] twoSumSorted(int[] arr, int target) {
    int left = 0, right = arr.length - 1;
    while (left < right) {
        int sum = arr[left] + arr[right];
        if (sum == target) return new int[]{left, right};
        else if (sum < target) left++;
        else right--;
    }
    return new int[]{-1, -1};
}

// 2. Sliding Window Example (Longest Subarray with Sum <= K)
int longestSubarray(int[] arr, int k) {
    int l = 0, sum = 0, maxLen = 0;
    for (int r = 0; r < arr.length; r++) {
        sum += arr[r];
        while (sum > k) sum -= arr[l++];
        maxLen = Math.max(maxLen, r - l + 1);
    }
    return maxLen;
}
```

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

```java
// 1. Backtracking Example (Generate All Subsets)
void backtrack(int idx, int[] nums, List<Integer> curr, List<List<Integer>> res) {
    res.add(new ArrayList<>(curr));
    for (int i = idx; i < nums.length; i++) {
        curr.add(nums[i]);                 // Choose
        backtrack(i + 1, nums, curr, res); // Explore
        curr.remove(curr.size() - 1);      // Un-choose (Backtrack)
    }
}

// 2. Dynamic Programming Example (0/1 Knapsack - Tabulation)
int knapsack(int W, int[] wt, int[] val, int n) {
    int[][] dp = new int[n + 1][W + 1];
    for (int i = 1; i <= n; i++) {
        for (int w = 1; w <= W; w++) {
            if (wt[i - 1] <= w) {
                dp[i][w] = Math.max(val[i - 1] + dp[i - 1][w - wt[i - 1]], dp[i - 1][w]);
            } else {
                dp[i][w] = dp[i - 1][w];
            }
        }
    }
    return dp[n][W];
}
```

### C. Graph Algorithms
* **BFS (Breadth-First Search):** `Queue` ka use karke level-by-level traversal; **unweighted graph mein shortest path** deta hai (`O(V + E)`).
* **DFS (Depth-First Search):** Recursion ya `Stack` se depth mein jaana; cycle detection, connected components, aur path finding (`O(V + E)`).
* **Dijkstra's Algorithm:** `PriorityQueue` (Min-Heap) ka use karke **non-negative weighted graph mein single-source shortest path** (`O(E log V)`).
* **Bellman-Ford & Floyd-Warshall:** Negative edge weights handle karne (`O(V * E)`) aur All-Pairs Shortest Path (`O(V^3)`) ke liye.
* **Topological Sort (Kahn's Algorithm / DFS):** Directed Acyclic Graph (DAG) mein dependencies ka linear order nikalne ke liye (`O(V + E)`).
* **Minimum Spanning Tree (Kruskal's & Prim's):** Poore graph ko minimum total edge weight se connect karne ke liye (`O(E log E)`).

```java
// 1. Standard BFS (Unweighted Shortest Path)
void bfs(int start, List<List<Integer>> adj, int n) {
    boolean[] visited = new boolean[n];
    Queue<Integer> q = new LinkedList<>();
    q.offer(start);
    visited[start] = true;
    
    while (!q.isEmpty()) {
        int node = q.poll();
        for (int nei : adj.get(node)) {
            if (!visited[nei]) {
                visited[nei] = true;
                q.offer(nei);
            }
        }
    }
}

// 2. Dijkstra's Algorithm (Weighted Shortest Path)
int[] dijkstra(int src, List<List<int[]>> adj, int n) {
    int[] dist = new int[n];
    Arrays.fill(dist, Integer.MAX_VALUE);
    dist[src] = 0;
    
    // int[] -> {node, distance}
    PriorityQueue<int[]> pq = new PriorityQueue<>((a, b) -> Integer.compare(a[1], b[1]));
    pq.offer(new int[]{src, 0});
    
    while (!pq.isEmpty()) {
        int[] curr = pq.poll();
        int u = curr[0], d = curr[1];
        if (d > dist[u]) continue;
        
        for (int[] edge : adj.get(u)) {
            int v = edge[0], weight = edge[1];
            if (dist[u] + weight < dist[v]) {
                dist[v] = dist[u] + weight;
                pq.offer(new int[]{v, dist[v]});
            }
        }
    }
    return dist;
}
```
