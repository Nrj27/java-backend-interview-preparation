# Java, Spring, Hibernate, SQL & DSA Interview Questions with Answers and Code

Each question has a short, interview-ready answer on the next line, followed by code to verify the concept.

## 1. Maven and Build

Q1. What is a Maven build?

Answer: Maven is a build automation tool used to manage dependencies, compile code, run tests, and package Java applications.

Code to verify:

bash

```bash
mvn --version
mvn clean package
```

Q2. What does `mvn clean install` do?

Answer: `clean` removes the target directory, `install` compiles, tests, packages, and installs the JAR/WAR into the local Maven repository.

Code to verify:

bash

```bash
mvn clean install
```

Q3. How do you push code to production?

Answer: Commit code, push to Git, raise a PR, complete code reviews, pass CI/CD pipelines, deploy through the release pipeline, and verify production health.

Code to verify:

bash

```bash
git add .
git commit -m "Release changes"
git push origin feature-branch
```

Q4. What is code coverage and line coverage?

Answer: Code coverage measures how much application code is executed by tests, while line coverage measures the percentage of executable lines executed.

Code to verify:

bash

```bash
mvn clean verify
```

Check the JaCoCo report at `target/site/jacoco/index.html`.

Q5. How do you improve code coverage when build fails?

Answer: Analyze JaCoCo reports, identify uncovered lines, write positive, negative, and edge-case unit tests, and fix failing tests.

Code to verify:

bash

```bash
mvn clean test
mvn jacoco:report
```

## 2. Testing

Q6. How do you verify a method is called twice in Mockito?

Answer: Use `verify()` with `times(2)` to check whether a mocked method was invoked exactly twice.

Code to verify:

java

```java
verify(userService, times(2)).getUser();
```

Q7. In which situations do you use PowerMock?

Answer: PowerMock is mainly used in legacy applications to mock static, private, final methods, and constructors that are difficult to mock using standard Mockito.

Code to verify:

java

```java
@RunWith(PowerMockRunner.class)
@PrepareForTest(Utility.class)
public class UtilityTest {
    @Test
    public void testStaticMethod() {
        PowerMockito.mockStatic(Utility.class);
        when(Utility.getValue()).thenReturn("Java");

        assertEquals("Java", Utility.getValue());
    }
}
```

## 3. Core Java

Q8. What is the difference between final keyword and final variable?

Answer: `final` is a keyword used to restrict inheritance, method overriding, or variable reassignment, while a final variable can be assigned only once.

Code to verify:

java

```java
final int number = 10;
// number = 20; // Compilation error
```

Q9. What is Garbage Collection in Java?

Answer: Garbage Collection automatically identifies unreachable objects and reclaims their heap memory.

Code to verify:

java

```java
class Test {
    public static void main(String[] args) {
        Test obj = new Test();
        obj = null;
        System.gc();
    }
}
```

Q10. How do you debug and fix OutOfMemoryError?

Answer: Analyze heap dumps using Eclipse MAT or VisualVM, identify memory leaks or large objects, optimize memory usage, and increase heap size only when justified.

Code to verify:

bash

```bash
jcmd <pid> GC.heap_dump heap.hprof
```

Q11. What are atomic variables in Java?

Answer: Atomic variables provide thread-safe operations such as increment and compare-and-set without requiring explicit synchronization.

Code to verify:

java

```java
AtomicInteger count = new AtomicInteger(0);

count.incrementAndGet();
System.out.println(count.get()); // 1
```

Q12. What is the volatile keyword?

Answer: `volatile` ensures that changes to a variable are visible across threads but does not guarantee atomicity.

Code to verify:

java

```java
class Shared {
    volatile boolean running = true;
}
```

Q13. What is the difference between volatile and synchronized?

Answer: `volatile` provides visibility of shared variables, whereas `synchronized` provides both visibility and mutual exclusion.

Code to verify:

java

```java
volatile boolean flag = true;

synchronized void update() {
    flag = false;
}
```

Q14. How do you avoid performance issues caused by synchronization?

Answer: Minimize synchronized blocks, reduce lock scope, avoid unnecessary shared state, and use atomic variables or concurrent collections.

Code to verify:

java

```java
AtomicInteger count = new AtomicInteger(0);

count.incrementAndGet();
```

Q15. What is a BlockingQueue and where do you use it in real applications?

Answer: BlockingQueue is a thread-safe queue used in producer-consumer applications where producers and consumers wait when the queue is full or empty.

Code to verify:

java

```java
BlockingQueue<Integer> queue =
    new ArrayBlockingQueue<>(2);

queue.put(10);
queue.put(20);

System.out.println(queue.take()); // 10
```

Q16. What changes did you make when migrating from Java 7 to Java 8?

Answer: I adopted Lambda expressions, Stream API, Functional Interfaces, Optional, default methods, and the new Date and Time API.

Code to verify:

java

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4);

numbers.stream()
       .filter(n -> n % 2 == 0)
       .forEach(System.out::println);
```

Q17. What are different ways to ensure thread safety?

Answer: Thread safety can be achieved using synchronization, volatile, atomic classes, immutable objects, ThreadLocal, and concurrent collections.

Code to verify:

java

```java
ConcurrentHashMap<Integer, String> map =
    new ConcurrentHashMap<>();

map.put(1, "Java");
System.out.println(map.get(1));
```

Q18. What is ThreadLocal and where is it used?

Answer: ThreadLocal maintains a separate variable copy for each thread and is commonly used for request context and thread-specific data.

Code to verify:

java

```java
ThreadLocal<String> user =
    ThreadLocal.withInitial(() -> "Admin");

System.out.println(user.get()); // Admin
user.remove();
```

## 4. Collections

Q19. What is the difference between HashMap and Hashtable?

Answer: HashMap is non-synchronized and allows one null key and multiple null values, whereas Hashtable is synchronized and does not allow null keys or values.

Code to verify:

java

```java
Map<Integer, String> map = new HashMap<>();
map.put(null, null);

System.out.println(map);
```

Q20. Why does Hashtable not allow null keys or values?

Answer: Hashtable explicitly rejects null keys and values because its implementation does not support null entries and treats null as invalid input.

Code to verify:

java

```java
Hashtable<Integer, String> table = new Hashtable<>();

table.put(null, "Java"); // NullPointerException
```

Q21. What is load factor in HashMap?

Answer: Load factor determines how full a HashMap can become before its internal bucket array is resized.

Code to verify:

java

```java
Map<Integer, String> map = new HashMap<>(16, 0.75f);
```

Q22. What does the default load factor 0.75 mean?

Answer: A default load factor of 0.75 means a HashMap with capacity 16 has a resize threshold of 12 entries.

Code to verify:

java

```java
Map<Integer, Integer> map = new HashMap<>(16, 0.75f);

for (int i = 1; i <= 12; i++) {
    map.put(i, i);
}
```

## 5. SQL

Q23. What is the difference between UNION and UNION ALL?

Answer: UNION removes duplicate records, whereas UNION ALL returns all records, including duplicates.

Code to verify:

sql

```sql
SELECT 'A' AS name
UNION
SELECT 'A';

SELECT 'A' AS name
UNION ALL
SELECT 'A';
```

Q24. What is the difference between LEFT JOIN and RIGHT JOIN?

Answer: LEFT JOIN returns all records from the left table and matching records from the right table, whereas RIGHT JOIN does the opposite.

Code to verify:

sql

```sql
SELECT *
FROM employees e
LEFT JOIN departments d
ON e.dept_id = d.id;
```

Q25. When do you use LEFT JOIN?

Answer: I use LEFT JOIN when I need all records from the primary table, even when matching records are unavailable in the second table.

Code to verify:

sql

```sql
SELECT e.name, d.department_name
FROM employees e
LEFT JOIN departments d
ON e.dept_id = d.id;
```

Q26. How do you find records in one table that have no relationship with another?

Answer: Use LEFT JOIN with IS NULL or NOT EXISTS to find records without matching entries in another table.

Code to verify:

sql

```sql
SELECT e.*
FROM employees e
LEFT JOIN departments d
ON e.dept_id = d.id
WHERE d.id IS NULL;
```

Q27. How do you handle NULL values and conditional mapping in SQL?

Answer: Use COALESCE or ISNULL for NULL replacement and CASE WHEN for conditional mapping.

Code to verify:

sql

```sql
SELECT
    COALESCE(name, 'Unknown') AS employee_name,
    CASE
        WHEN salary > 50000 THEN 'High'
        ELSE 'Low'
    END AS salary_category
FROM employees;
```

Q28. How do you map values like A to Apple, B to Banana in SQL?

Answer: Use CASE WHEN to map specific values to corresponding descriptions.

Code to verify:

sql

```sql
SELECT
    CASE code
        WHEN 'A' THEN 'Apple'
        WHEN 'B' THEN 'Banana'
        ELSE 'Unknown'
    END AS fruit
FROM products;
```

Q29. How do you remove duplicates in SQL?

Answer: Use DISTINCT to retrieve unique records or ROW\_NUMBER() to identify and remove duplicate rows based on selected columns.

Code to verify:

sql

```sql
SELECT DISTINCT name
FROM employees;
```

## 6. Hibernate

Q30. How do you define relationships between tables in Hibernate?

Answer: Hibernate defines relationships between entities using annotations such as @OneToOne, @OneToMany, @ManyToOne, and @ManyToMany.

Code to verify:

java

```java
@Entity
class Employee {

    @Id
    @GeneratedValue
    private Long id;

    @ManyToOne
    @JoinColumn(name = "department_id")
    private Department department;
}
```

Q31. What are the types of relationships in Hibernate?

Answer: Hibernate supports four main relationships: One-to-One, One-to-Many, Many-to-One, and Many-to-Many.

Code to verify:

java

```java
@OneToOne
private Passport passport;

@OneToMany
private List<Order> orders;

@ManyToOne
private Department department;

@ManyToMany
private List<Role> roles;
```

## 7. Spring

Q32. What is the difference between constructor injection and setter injection?

Answer: Constructor injection is preferred for mandatory dependencies and immutability, whereas setter injection is useful for optional dependencies.

Code to verify:

java

```java
@Service
class UserService {

    private final UserRepository repository;

    public UserService(UserRepository repository) {
        this.repository = repository;
    }
}
```

Q33. What happens if you do not use @Autowired in Spring?

Answer: If a Spring bean has only one constructor, Spring automatically injects its dependencies without requiring @Autowired.

Code to verify:

java

```java
@Service
class UserService {

    private final UserRepository repository;

    public UserService(UserRepository repository) {
        this.repository = repository;
    }
}
```

Q34. How do you perform constructor injection without @Autowired?

Answer: Define a single parameterized constructor in the Spring bean, and Spring automatically resolves and injects the required dependencies.

Code to verify:

java

```java
@Component
class EmployeeService {

    private final EmployeeRepository repository;

    EmployeeService(EmployeeRepository repository) {
        this.repository = repository;
    }
}
```

## 8. DSA

Q35. Find the longest substring without repeating characters in Java?

Answer: Use the Sliding Window algorithm with a HashMap to track character positions and find the longest substring in O(n) time complexity.

Code to verify:

java

```java
import java.util.*;

public class LongestSubstring {

    public static int longest(String s) {

        Map<Character, Integer> map = new HashMap<>();

        int left = 0;
        int maxLength = 0;

        for (int right = 0; right < s.length(); right++) {

            char ch = s.charAt(right);

            if (map.containsKey(ch)) {
                left = Math.max(left, map.get(ch) + 1);
            }

            map.put(ch, right);

            maxLength = Math.max(
                maxLength,
                right - left + 1
            );
        }

        return maxLength;
    }

    public static void main(String[] args) {

        System.out.println(longest("abcabcbb")); // 3
        System.out.println(longest("bbbbb"));    // 1
        System.out.println(longest("pwwkew"));   // 3
        System.out.println(longest("abcdef"));   // 6
    }
}
```

Interview preparation tip: Focus especially on Java 8 Streams, HashMap internals, Multithreading, Java Collections, Spring Dependency Injection, Hibernate relationships, SQL Joins, Mockito, and Sliding Window DSA problems. These topics are useful for explaining both concepts and real project experience.
