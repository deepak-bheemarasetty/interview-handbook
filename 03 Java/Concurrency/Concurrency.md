```table-of-contents
```

## Concurrency Overview
1. Concurrency means a program can make progress on more than one task at the same time.
2. Java supports concurrency through threads and the `java.util.concurrent` package.
3. The tutorial focuses first on low-level thread basics, then on higher-level concurrency tools.

## Processes and Threads
1. A process is a self-contained execution environment with its own memory space.
2. A thread is a unit of execution inside a process.
3. Threads share the process memory and open files, which makes communication fast but also risky.
4. A thread is often called a lightweight process because it needs fewer resources than a process.
5. A single-core CPU can still run concurrent tasks by switching between them using time slicing.

## Thread Basics
1. Every Java application starts with at least one thread, the main thread.
2. Each thread is represented by an instance of `Thread`.
3. There are two common ways to handle work in Java:
   1. Create and manage `Thread` objects directly.
   2. Pass tasks to an executor and let it manage the threads.

## Creating Threads
1. `Runnable` represents a task that can run, but it does not return a result.
2. `Callable` also represents a task, but it can return a result and throw checked exceptions.
3. `Thread` is the actual thread object that can execute a task.
4. In practice, tasks and thread management are often kept separate.

## Thread Objects
1. `Thread.sleep(...)` pauses the current thread for a while.
2. Sleep time is not guaranteed to be exact because the OS controls scheduling.
3. `sleep()` can end early if the thread is interrupted.
4. `interrupt()` is a way to set the interrupted status of a thread.
5. `join()` makes one thread wait for another thread to finish.
6. `join()` can also be interrupted.

## Synchronization
1. Threads usually communicate by sharing data.
2. Shared data can cause two common problems:
   1. Thread interference
   2. Memory consistency errors
3. Synchronization helps prevent these problems.
4. Synchronization can also create thread contention when many threads compete for the same resource.

## Thread Interference
1. Thread interference happens when multiple threads access the same mutable data and the result becomes inconsistent.
2. This usually happens when a read-modify-write operation is not protected.

## Memory Consistency Errors
1. A memory consistency error happens when threads see different or stale views of shared data.
2. This can happen even when the code looks logically correct.
3. Synchronization helps create the visibility guarantees needed for correct results.

## synchronized
1. A `synchronized` method or block allows only one thread at a time to use the protected code for the same lock.
2. Every object has an intrinsic lock, also called a monitor lock.
3. A thread must acquire the lock before entering synchronized code guarded by that lock.
4. Exiting a synchronized method or block creates a happens-before relationship with later synchronized access on the same lock.
5. This helps ensure that changes made by one thread become visible to other threads.
6. `synchronized` can protect both mutual exclusion and visibility.

## volatile
1. A `volatile` variable gives visibility guarantees between threads.
2. When one thread writes to a volatile variable, other threads reading it see the latest value.
3. `volatile` does not replace `synchronized` for compound actions like incrementing a counter.
4. `volatile` is useful for status flags and simple coordination.

## Atomic Access
1. An atomic action happens as one indivisible step.
2. Atomicity means other threads cannot observe a partially completed action.
3. Not all operations are atomic.
4. A `volatile` read or write is atomic for the variable itself, but a larger operation like `count++` is not atomic.

## Liveness
1. Liveness means a concurrent program can keep making progress in a timely way.
2. Deadlock happens when two or more threads wait forever for each other.
3. Starvation happens when a thread keeps getting blocked and never gets a chance to run.
4. Livelock happens when threads keep responding to each other but still make no progress.

## High Level Concurrency Objects
1. Java also provides higher-level tools in `java.util.concurrent`.
2. These tools reduce the need to manage low-level locking manually.
3. Important examples include:
   1. Lock objects
   2. Executors
   3. Thread pools
   4. Fork/Join
   5. Concurrent collections
   6. Atomic variables

## Concurrent Collections
1. Concurrent collections are designed for safe use by multiple threads.
2. `ConcurrentHashMap` is the standard concurrent analog of `HashMap`.
3. `ConcurrentSkipListMap` is the standard concurrent analog of `TreeMap`.
4. `BlockingQueue` is a queue that can block when inserting into a full queue or removing from an empty one.
5. Concurrent collections help reduce synchronization problems and improve scalability.

## Interview Takeaway
1. Threads share memory, so concurrency problems often come from shared mutable state.
2. Use `synchronized` when you need both mutual exclusion and visibility.
3. Use `volatile` when you only need visibility for a simple shared value.
4. Use higher-level concurrent utilities when possible instead of manually managing thread safety.