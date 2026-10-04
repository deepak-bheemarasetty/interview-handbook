# LinkedList

> [!abstract] Overview
> `LinkedList` is a doubly linked implementation of `List` and `Deque`. It supports efficient insertion and removal at the ends, but it is usually a poor default choice because traversal is slow and each element has node-object overhead.

## Key Facts

| Property | Details |
| --- | --- |
| Package | `java.util` |
| Implements | `List`, `Deque`, `Queue` |
| Internal structure | Doubly linked nodes (`prev`, `item`, `next`) |
| Allows `null` | Yes, including multiple `null` elements |
| Thread-safe | No |
| Random access | No; it does not implement `RandomAccess` |

## Internal Structure

Each element is held in a separate node. A node stores the value plus links to the previous and next nodes. The list maintains references to its first and last nodes.

```text
null <- [prev | A | next] <-> [prev | B | next] <-> [prev | C | next] -> null
         first                                           last
```

This makes adding or removing at either end efficient. However, reaching an element by index requires walking node by node from the closer end.

## Time Complexity

| Operation | Time | Why |
| --- | --- | --- |
| `addFirst()` / `addLast()` | `O(1)` | Updates end-node links |
| `removeFirst()` / `removeLast()` | `O(1)` | Updates end-node links |
| `get(index)` / `set(index, value)` | `O(n)` | Traverses nodes to the index |
| `add(index, value)` | `O(n)` | Must first traverse to the position |
| `remove(index)` | `O(n)` | Must first traverse to the position |
| `contains(value)` | `O(n)` | Sequential traversal |

> [!warning] Common misconception
> Linked lists do **not** make indexed insertion or deletion automatically `O(1)`. The link update is `O(1)` only after the target node is already known; finding that node through the `List` API is `O(n)`.

## LinkedList vs ArrayList

| Aspect | `ArrayList` | `LinkedList` |
| --- | --- | --- |
| Storage | Contiguous resizable array | Separate doubly linked nodes |
| Indexed access | `O(1)` | `O(n)` |
| Append | Amortized `O(1)` | `O(1)` |
| Insert/remove at start | `O(n)` due to shifting | `O(1)` |
| Memory overhead | Lower per element | Higher: node object and two links |
| Cache locality | Good | Poor; nodes are scattered in memory |
| Typical default | Usually preferred | Rarely the right default |

`ArrayList` is normally faster in practice, even for some operations where both have the same Big-O complexity. Its elements are stored together, which is more CPU-cache friendly and avoids a node allocation per element.

## LinkedList vs ArrayDeque

Both can be used as a queue or deque, but prefer `ArrayDeque` in almost all ordinary stack and queue cases.

| Aspect | `LinkedList` | `ArrayDeque` |
| --- | --- | --- |
| End operations | `O(1)` | Amortized `O(1)` |
| Allows `null` | Yes | No |
| Memory layout | Per-node objects and links | Resizable circular array |
| Cache locality | Poor | Good |
| Typical queue/stack choice | Usually avoid | Preferred |

`ArrayDeque` has lower allocation and memory overhead, and usually better real-world performance. Choose `LinkedList` only when its `List` and `Deque` semantics together are specifically needed and the trade-offs are understood.

## Important API Operations

| Need | Preferred method | Notes |
| --- | --- | --- |
| Add at front | `addFirst()` / `offerFirst()` | `offerFirst()` returns `false` on capacity failure; capacity is not normally a concern here |
| Add at end | `addLast()` / `offerLast()` | `add()` is equivalent to `addLast()` |
| Read first | `getFirst()` / `peekFirst()` | `getFirst()` throws if empty; `peekFirst()` returns `null` |
| Remove first | `removeFirst()` / `pollFirst()` | `removeFirst()` throws if empty; `pollFirst()` returns `null` |
| Stack operations | `push()`, `pop()`, `peek()` | Operate at the head |

> [!tip] API choice
> Use `offer`, `poll`, and `peek` when an empty-result value is appropriate. Use `add`, `remove`, and `element` when an exceptional state should be reported with an exception.

## When To Use It

- You need `Deque` operations and must permit `null` values.
- You already have a node reference internally and need to relink nodes, though Java's public `LinkedList` API does not expose nodes.
- You have a specific, measured reason to prefer it.

## When Not To Use It

- You need frequent indexed reads or iteration over large collections.
- You need a default `List`: use `ArrayList`.
- You need a stack, queue, or deque: use `ArrayDeque`.
- You need thread safety: use an appropriate concurrent collection or external synchronization.

## Interview Questions

### Why is `LinkedList.get(index)` `O(n)`?

Nodes do not have array-style addresses. The implementation must traverse from the first or last node until it reaches the requested index.

### Why is `LinkedList` often slower than `ArrayList` despite `O(1)` end operations?

Every `LinkedList` element requires a separate node allocation and pointer links. Traversal follows references across memory, which has poor cache locality. `ArrayList` stores elements contiguously and is usually more CPU-cache friendly.

### Is insertion in a linked list always `O(1)`?

No. Inserting after a known node is `O(1)`, but locating a position by index in Java's `LinkedList` is `O(n)`. Therefore `add(index, value)` is `O(n)`.

### Why prefer `ArrayDeque` over `LinkedList` for queues and stacks?

`ArrayDeque` uses a circular array, avoids per-node allocation, has better cache locality, and is generally faster. `LinkedList` is mainly useful when its ability to store `null` matters or there is a specific reason to use it.

## Common Mistakes

See [[13 Mistake Log/Mistakes Log#LinkedList|LinkedList mistakes]].

## Related Topics

- [[03 Java/Collections/01 Collections Framework|01 Collections Framework]]
- [[03 Java/Collections/03 ArrayList|03 ArrayList]]
- [[03 Java/Collections/06 Queue|06 Queue]]
- [[03 Java/Collections/02 HashMap|02 HashMap]]
