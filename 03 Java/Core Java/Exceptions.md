## Overview

Exceptions separate normal business flow from failure handling. Catch an exception only where the program can recover, translate it, or add useful context.

## Checked vs Unchecked

| Type | Base class | Caller must handle/declare? | Typical use |
|---|---|---:|---|
| Checked | `Exception` (not `RuntimeException`) | Yes | recoverable external condition, such as I/O |
| Unchecked | `RuntimeException` | No | programming error, invalid state, bad input contract |
| Error | `Error` | No | serious JVM/system failure; usually do not catch |

## Propagation and Translation

An exception bubbles up the call stack until handled. At a boundary, translate low-level details into a domain-appropriate exception while retaining the original cause:

```java
throw new OrderPersistenceException("Could not save order", sqlException);
```

Do not swallow exceptions. Logging and rethrowing at every layer creates duplicate, noisy logs; log where the error is finally handled.

## try-with-resources

Use it for `AutoCloseable` resources such as streams, JDBC connections, statements, and result sets. Resources close in reverse creation order, even when the body throws.

```java
try (Connection connection = dataSource.getConnection()) {
    // use connection
}
```

## Interview Takeaway

Checked exceptions communicate a recoverable condition in an API; unchecked exceptions usually signal a violated precondition or invalid state. Preserve causes and use try-with-resources for deterministic cleanup.

```table-of-contents
```
