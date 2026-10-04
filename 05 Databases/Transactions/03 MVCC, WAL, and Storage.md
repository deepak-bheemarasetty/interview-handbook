## Overview

Database internals explain why transactions can be both correct and fast. Implementations differ, but MVCC, write-ahead logging, buffer caches, and storage engines are common concepts.

## MVCC

Multi-Version Concurrency Control keeps versions of rows so readers can often use a consistent snapshot without blocking writers. Old versions must eventually be cleaned up; long-running transactions can delay that cleanup. MVCC reduces read/write contention but does not remove the need to handle write conflicts.

## WAL and Recovery

With write-ahead logging, a change is recorded in durable log storage before its changed data page is written. After a crash, the database uses the log to redo committed work and undo incomplete work. This is central to durability and crash recovery.

## Buffer Pool and Storage Engine

The buffer pool caches disk pages in memory; a cache hit avoids slow storage I/O. A storage engine determines how data, indexes, locks, and recovery are implemented. Query performance often depends on page access patterns, not only CPU-level algorithm complexity.

## Interview Takeaway

MVCC provides snapshots, WAL makes recovery possible, and the buffer pool makes repeated page access fast. These mechanisms have resource and cleanup costs.

```table-of-contents
```
