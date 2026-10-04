```table-of-contents
```

## JVM Fundamentals
1. The JVM executes Java bytecode.
2. Java source code is compiled into `.class` bytecode files.
3. The JVM is one part of the Java platform; the JDK includes tools for development and the JRE provides the runtime.
4. The JVM specification defines an abstract machine, not one fixed implementation.
5. Platform independence comes from bytecode running on different JVM implementations.
6. The JVM is responsible for class loading, bytecode execution, runtime memory management, and garbage collection.
7. HotSpot is the most common JVM implementation and uses adaptive optimization.

## Execution Flow
1. `.java` files are compiled into `.class` files.
2. The JVM loads the class.
3. The JVM links and initializes the class.
4. The JVM then executes the bytecode using interpretation and JIT compilation.
5. The runtime may load supporting classes on demand as execution progresses.

## Interview Takeaway
1. Always explain the path from source code to execution.
2. Be clear on the difference between JVM, JRE, and JDK.
3. Mention that the JVM specification is abstract and vendor implementations vary internally.
