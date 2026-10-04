```table-of-contents
```

## Class Loading
1. The JVM dynamically loads, links, and initializes classes and interfaces.
2. Loading means finding the binary representation of a class and creating a runtime class from it.
3. Linking means preparing the class for execution.
4. Initialization runs the class initialization method, often called `<clinit>`.
5. The JVM specification describes class loading behavior, but exact loader implementations can differ.

## Linking
1. Verification checks that the bytecode is valid and safe to execute.
2. Preparation allocates memory for class variables and sets default values.
3. Resolution converts symbolic references into direct references.
4. Verification helps prevent malformed or unsafe class files from executing.

## Class Loaders
1. The bootstrap class loader loads core Java classes.
2. User-defined class loaders can load application-specific classes.
3. Parent delegation helps avoid duplicate loading and protects core classes.
4. The platform class loader loads platform modules and libraries.
5. Custom class loaders are useful for plugins, isolation, and dynamic loading.

## When Classes Initialize
1. A class is initialized when it is first actively used.
2. Common triggers include instance creation, static field access, and static method calls.
3. Class initialization is not the same as class loading.

## Interview Takeaway
1. Know the difference between loading, linking, and initialization.
2. Be able to explain parent delegation clearly.
3. Remember that verification, preparation, and resolution are the three linking steps.
