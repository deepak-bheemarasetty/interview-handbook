
## Overview

### Collection

A **Collection** is an object that represents a group of individual objects as a single unit.

### Java Collections Framework (JCF)

The Java Collections Framework is a unified architecture for storing and manipulating groups of objects. It is **not** just a hierarchy of interfaces — it includes interfaces, concrete implementations, abstract classes, iterators, and utility algorithms.

---

## Why It Exists

Before JCF, Java had many ad-hoc collection classes (`Vector`, `Hashtable`, `Stack`) with inconsistent APIs. JCF was introduced to:

- Standardize data structures through common interfaces
- Promote code reuse across implementations
- Allow algorithms to work on any collection type
- Improve maintainability through programming to interfaces

---

## What Makes Up the JCF

| Component | Role | Example |
|-----------|------|---------|
| Interfaces | Define contracts | `List`, `Set`, `Map` |
| Implementations | Store data | `ArrayList`, `HashMap` |
| Abstract classes | Partial implementations | `AbstractList`, `AbstractMap` |
| Iterators | Traverse elements | `Iterator`, `ListIterator` |
| Utility algorithms | Operate on collections | `Collections.sort()` |

---

## Framework Design Philosophy

Java separates responsibilities:

```
Interfaces        →  Define contracts
Implementations   →  Store data
Collections class →  Provide algorithms
```

This separation promotes code reuse and maintainability. Implementations do not reimplement sorting, searching, or synchronization — the `Collections` utility class provides those algorithms once.

---

## Architecture

```
Iterable
    │
Collection
├── List
├── Set
└── Queue

Map (Separate Hierarchy)
```

> **Note:** `Iterable` is not part of the Collections Framework but serves as its foundation.

---

## Why Does Collection Extend Iterable?

`Iterable` defines the ability to iterate over elements.

Since every collection should support iteration, `Collection` extends `Iterable`. This enables:

- Enhanced for-loop (`for-each`)
- Iterator API
- Generic algorithms that work on any iterable object

**Key idea:** Collection inherits the ability to iterate instead of redefining iteration behavior in every subinterface.

---

## Collection Interfaces

### Collection

Root interface representing a group of objects.

Subinterfaces: `List`, `Set`, `Queue`

### Map

`Map` belongs to the JCF but is **not** a subtype of `Collection`.

| Collection | Map |
|------------|-----|
| Stores individual elements | Stores key-value pairs |
| `add()` | `put()` |
| `remove()` | `remove(key)` |
| `contains()` | `containsKey()` |

**Why?** Structure and APIs are fundamentally different.

---

## Collection vs Collections

Java separates responsibilities:

| | Collection | Collections |
|---|------------|-------------|
| **What** | Interface | Utility class |
| **Role** | Defines the contract | Provides reusable algorithms |
| **Methods** | Instance methods on implementations | Static utility methods |
| **State** | Implementations hold data | Stateless — operates on supplied collection |

### Why Both Exist

Implementations should not each reimplement sorting, binary search, or synchronization. The `Collections` class centralizes these algorithms so every implementation benefits.

### Why Collections Methods Are Static

`Collections` methods are static because they are stateless utility algorithms. They operate on the supplied collection rather than maintaining internal state. Creating a `Collections` object would provide no additional value.

### Common Utility Methods

- `sort()`, `shuffle()`, `reverse()`, `binarySearch()`
- `min()`, `max()`, `frequency()`
- `synchronizedList()`, `unmodifiableList()`

> **Correction:** `Collections.filter()` does **not** exist. Filtering belongs to the **Stream API**.

---

## Programming to Interfaces

Instead of:

```java
ArrayList<Employee> employees = new ArrayList<>();
```

Prefer:

```java
List<Employee> employees = new ArrayList<>();
```

### Benefits

- Loose coupling
- Open/Closed Principle — extend behavior without modifying existing code
- Easier testing — mock interfaces, not concrete classes
- Easier maintenance
- Framework compatibility
- Implementation replacement without changing business logic

---

## Spring Connection

Spring commonly depends on interfaces rather than implementations.

```java
private final List<NotificationService> notificationServices;
```

Spring:

1. Finds every bean implementing `NotificationService`
2. Creates a collection of those beans
3. Injects the collection

The application depends only on the `List` interface while Spring chooses the implementation. This is programming to interfaces in production.

---

## Comparable vs Comparator

| | Comparable | Comparator |
|---|------------|------------|
| **Ordering** | Natural ordering | External/custom ordering |
| **Method** | `compareTo()` | `compare()` |
| **Defined in** | The class itself | Separate class or lambda |
| **Count** | One natural ordering | Multiple sorting strategies |

`Collections.sort()` works only when:

- Elements implement `Comparable`, **or**
- A `Comparator` is supplied

Java never automatically chooses which field to sort on.

---

## Collection Implementations

| Implementation       | Internal Structure       |  Ordered  | Sorted | Duplicates  | Thread Safe | Primary Complexity     |
| -------------------- | ------------------------ | :-------: | :----: | :---------: | :---------: | ---------------------- |
| ArrayList            | Dynamic Array            |     ✅     |   ❌    |      ✅      |      ❌      | O(1) random access     |
| LinkedList           | Doubly Linked List       |     ✅     |   ❌    |      ✅      |      ❌      | O(n) random access     |
| Vector               | Dynamic Array            |     ✅     |   ❌    |      ✅      |      ✅      | O(1) random access     |
| CopyOnWriteArrayList | Copy-on-Write Array      |     ✅     |   ❌    |      ✅      |      ✅      | Read O(1), Write O(n)  |
| HashSet              | HashMap (keys only)      |     ❌     |   ❌    |      ❌      |      ❌      | O(1) average           |
| LinkedHashSet        | LinkedHashMap            |     ✅     |   ❌    |      ❌      |      ❌      | O(1) average           |
| TreeSet              | Red-Black Tree           |     ❌     |   ✅    |      ❌      |      ❌      | O(log n)               |
| PriorityQueue        | Binary Heap              | Priority  |   ❌    |      ✅      |      ❌      | O(log n) insert/remove |
| ArrayDeque           | Circular Array           | FIFO/LIFO |   ❌    |      ✅      |      ❌      | O(1) at ends           |
| HashMap              | Hash Table               |     ❌     |   ❌    | Keys unique |      ❌      | O(1) average           |
| LinkedHashMap        | Hash Table + Linked List |     ✅     |   ❌    | Keys unique |      ❌      | O(1) average           |
| TreeMap              | Red-Black Tree           |     ❌     |   ✅    | Keys unique |      ❌      | O(log n)               |
| ConcurrentHashMap    | Concurrent Hash Table    |     ❌     |   ❌    | Keys unique |      ✅      | O(1) average           |

---

## Choosing the Right Implementation

Analyze requirements first: read/write patterns, ordering, concurrency, and time complexity.

| Choose | When |
|--------|------|
| **HashMap** | Fast lookup, no ordering required |
| **ConcurrentHashMap** | Multiple threads need thread-safe map access |
| **TreeMap** | Sorted keys or ordered traversal required |
| **ArrayList** | Frequent random access, mostly reads |
| **LinkedList** | Frequent insert/delete when you already have the node reference |
| **HashSet** | Unique elements, no ordering |
| **TreeSet** | Unique elements, sorted order |
| **ArrayDeque** | FIFO queue or LIFO stack |
| **PriorityQueue** | Elements processed by priority, not arrival order |

### Decision Checklist

- Does data need insertion order preserved?
- Must elements be unique?
- Is fast lookup required?
- Must data be sorted?
- Are key-value pairs needed?
- Is thread safety required?

### Requirement-Driven Thinking

Choose a collection based on the dominant query pattern, not just its headline complexity.

Examples:

- `HashSet` when uniqueness and fast membership checks matter
- `TreeMap` when ordered queries matter
- multiple collections when one structure cannot satisfy all operations efficiently

### Multiple Indexes

Sometimes one collection is not enough.

If an application needs both fast lookup and ordered queries, maintaining more than one index can be a better design than forcing a single collection to do everything.

Example pattern:

- `HashMap` for fast lookup
- `TreeMap` for ordered access
- `PriorityQueue` for top-k or next-item processing

---

## HashMap Rehashing

When the load factor threshold is exceeded:

```
HashMap
  ↓
Resizes internal array
  ↓
Rehashes existing entries into new buckets
  ↓
Reduces future collisions
```

**Important distinction:** Collisions happen during normal operation. Rehashing happens when the table **resizes** — it is not the same as collision resolution.

> **Correction:** HashMap does not simply "redistribute buckets." It resizes and rehashes all entries.

> **Full topic:** See [[HashMap Internals]].

---

## ConcurrentHashMap

ConcurrentHashMap is **not** a synchronized `HashMap`.

| | Synchronized HashMap | ConcurrentHashMap |
|---|---------------------|-------------------|
| Lock scope | Entire map | Fine-grained (segment/bucket level) |
| Read concurrency | Blocked during writes | High — reads rarely block |
| Thread safety | Yes | Yes |
| Performance under contention | Poor | Much better |

Use when multiple threads read and write a shared map concurrently. Compound operations still require `computeIfAbsent()` or external synchronization.

> **Full topic:** See [[ConcurrentHashMap]].

---

## PriorityQueue

PriorityQueue uses a binary heap — elements are retrieved by **priority**, not arrival order.

**Correction:** PriorityQueue does **not** guarantee FIFO ordering for elements with equal priority. If FIFO among equal priorities is required, additional ordering logic is needed (e.g., tie-breaker in `Comparator` or a secondary queue).

---

## API Guarantees vs Assumptions

Always distinguish between:

- What Java **guarantees**
- What **usually** happens
- What developers **assume**

| Topic | Guarantee | Common Assumption (Wrong) |
|-------|-----------|---------------------------|
| HashMap lookup | O(1) **average** | Always O(1) |
| PriorityQueue | Priority ordering | FIFO for equal priorities |
| Collections utility | Specific static methods exist | `filter()` exists on Collections |
| Sorting | Requires Comparable or Comparator | Java picks a field automatically |

---

## Common Interview Questions

### Q1. Why was the Collections Framework introduced?

To provide a unified architecture for storing and manipulating groups of objects — standard APIs, reusable implementations, and generic algorithms — while improving maintainability.

### Q2. Collection vs Collections?

**Collection** is the root interface defining the contract. **Collections** is a utility class providing static, stateless algorithms (`sort`, `shuffle`, `binarySearch`). Java separates contract from algorithm to avoid reimplementing utilities in every collection class.

### Q3. Why isn't Map part of Collection?

Map stores key-value pairs; Collection stores individual elements. APIs differ fundamentally (`put` vs `add`, `containsKey` vs `contains`).

### Q4. List vs Set vs Queue vs Map?

- **List** — Ordered, allows duplicates, index-based access
- **Set** — Unique elements; ordering depends on implementation
- **Queue** — Process elements in a defined order (FIFO, LIFO, or priority)
- **Map** — Key-value pairs with efficient key-based lookup

### Q5. How do you choose the right implementation?

Analyze time complexity, memory, ordering, thread safety, and read/write patterns. See [Choosing the Right Implementation](#choosing-the-right-implementation).

### Follow-up Questions

**Why does ArrayList usually outperform LinkedList for iteration?**

ArrayList stores elements contiguously in memory, improving CPU cache locality. LinkedList nodes are scattered — each access may cause a cache miss and requires pointer traversal. Although LinkedList is O(1) for insert/delete with a node reference, ArrayList wins for most real-world read-heavy workloads.

**When should you use ConcurrentHashMap?**

When multiple threads need concurrent read/write access to a shared map. It provides thread safety with fine-grained synchronization — not a global lock on the entire map.

**Why doesn't HashSet preserve insertion order?**

HashSet is backed by HashMap. Elements are placed in hash buckets by hash code, not insertion sequence. Use LinkedHashSet for insertion order.

**Why is TreeMap slower than HashMap?**

TreeMap uses a Red-Black Tree — O(log n) operations. HashMap uses hashing — O(1) average. TreeMap pays the cost to maintain sorted order. Choose TreeMap when sorted keys or range queries matter.

---

## Real-World Usage

| Implementation | Use Case |
|----------------|----------|
| ArrayList | Shopping cart, search results, API response lists |
| HashMap | Caching, lookup tables, configuration |
| ConcurrentHashMap | Shared caches, registries in multi-threaded services |
| PriorityQueue | Job scheduling, task processing, event prioritization |
| TreeMap | Leaderboards, rankings, time-series keyed data |
| ArrayDeque | BFS queues, undo stacks |

---

## Common Mistakes [[Mistakes Log#Collection Framework Mistakes]]

---

## Related Topics

- [[HashMap Internals]]
- [[03 Java/Collections/03 ArrayList|03 ArrayList]]
- [[03 Java/Collections/07 LinkedList|07 LinkedList]]
- [[03 Java/Collections/04 HashSet|04 HashSet]]
- [[03 Java/Collections/05 TreeMap|05 TreeMap]]
- [[ConcurrentHashMap]]
- [[Comparable vs Comparator]]
- [[Knowledge Map]]

---

## Revision History

| Revision | Date | Confidence | Notes |
|----------|------|------------|-------|
| Initial study | 2026-07-09 | ⭐⭐⭐☆☆ | First handbook page |
| Day 1 session | 2026-07-10 | ⭐⭐⭐⭐☆ | Weak area drill, corrections, Spring connection, decision patterns |
| Day 3 review | | | |
| Day 7 review | | | |
| Day 14 review | | | |
| Day 30 review | | | |
