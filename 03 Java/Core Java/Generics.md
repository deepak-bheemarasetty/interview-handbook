```table-of-contents
```

# Generics

## Overview

1. Generics let classes, interfaces, and methods work with types as parameters.
2. They let you write reusable code for many types without losing compile-time type safety.

## Why It Is Used

1. Generics catch type errors at compile time instead of runtime.
2. They reduce repeated code by letting one algorithm work for many types.

## Core Terms

1. A **generic type** is a class or interface that is parameterized by types.
2. A **type parameter** is the placeholder declared in the generic definition, such as `T` in `Box<T>`.
3. A **type argument** is the real type supplied when using the generic type, such as `String` in `Box<String>`.
4. A type parameter must be a non-primitive type.

## Raw Types

1. A raw type is the name of a generic class or interface without type arguments.
2. Raw types are allowed for backward compatibility, but they remove compile-time type checks.
3. Using raw types can lead to unchecked warnings and runtime type errors.

```java
Box<Integer> intBox = new Box<>();
Box rawBox = new Box(); // raw type

Box<String> stringBox = new Box<>();
Box rawFromTyped = stringBox; // OK
Box<Integer> intBox2 = rawBox; // unchecked conversion warning
```

## Generic Methods

1. A generic method declares its own type parameters.
2. The scope of those type parameters is limited to that method.
3. Generic methods can be static or instance methods.
4. The type parameter list must appear before the return type.

```java
public class Util {
    public static <K, V> boolean compare(Pair<K, V> p1, Pair<K, V> p2) {
        return p1.getKey().equals(p2.getKey()) &&
               p1.getValue().equals(p2.getValue());
    }
}
```

## Bounded Type Parameters

1. A bounded type parameter restricts which types can be used as type arguments.
2. Use `extends` to declare the upper bound.
3. A bounded type parameter can use the methods of its upper bound.
4. A type parameter can have multiple bounds.

```java
class Box<T extends Comparable<T>> {
    // ...
}
```

## Generics and Subtyping

1. `MyClass<A>` and `MyClass<B>` are not related just because `A` and `B` are related.
2. Generic types are invariant by default.
3. If you need a relationship between different parameterized types, use wildcards.

## Type Inference

1. Type inference lets the compiler figure out type arguments from context.
2. The compiler uses invocation arguments, target types, and expected return types.
3. The diamond operator `<>` lets the compiler infer constructor type arguments when the context is clear.
4. Target typing helps the compiler infer types from assignment context and method arguments.

```java
List<String> list = Collections.emptyList();
```

## Wildcards

1. A wildcard represents an unknown type.
2. Wildcards are useful when you want flexibility without giving up type safety.
3. Wildcards are usually better for parameters than for return types.

### Upper Bounded Wildcards

1. Use `? extends T` when you want to read values from a structure.
2. It means the exact subtype is unknown.
3. You can safely read values as `T`, but you cannot safely add non-null values.

### Lower Bounded Wildcards

1. Use `? super T` when you want to add values to a structure.
2. It means the structure can accept `T` or any subtype of `T`.
3. Reading is limited because the exact type is unknown.

### PECS Rule

- Producer -> `? extends T`
- Consumer -> `? super T`

## Wildcard Capture

1. Sometimes the compiler needs help to capture an unknown wildcard type.
2. A helper method can allow the compiler to infer the exact captured type.

```java
class WildcardFixed {
    void foo(List<?> list) {
        fooHelper(list);
    }

    private <T> void fooHelper(List<T> list) {
        list.set(0, list.get(0));
    }
}
```

## Type Erasure

1. Java uses type erasure to implement generics.
2. The compiler replaces type parameters with their upper bound or `Object` if there is no bound.
3. The compiler inserts casts where needed.
4. The compiler may generate bridge methods to preserve polymorphism.
5. Generics do not create new runtime classes for each type argument.

### Bridge Methods

1. A bridge method is a compiler-generated helper method.
2. It keeps method overriding working after type erasure.
3. It forwards the erased method call to the real generic method.
4. You do not write bridge methods yourself; the compiler adds them when needed.

## Effects of Type Erasure

1. `Node<T>` becomes a raw-erased form at runtime.
2. `Node<T extends Comparable<T>>` erases to use the upper bound.
3. Generic methods also erase their type parameters.
4. Bridge methods can help method overriding continue to work after erasure.

## Restrictions on Generics

1. You cannot instantiate generic types with primitive types.
2. You cannot create instances of type parameters.
3. You cannot declare static fields whose types are type parameters.
4. You cannot use `cast` or `instanceof` with parameterized types in the normal way.
5. You cannot create arrays of parameterized types.
6. You cannot create, catch, or throw objects of parameterized types.
7. You cannot overload methods whose erased signatures would be the same.

## Interview Takeaway

If asked about generics, start with the problem they solve: reusable code with compile-time type safety. Then explain type parameters, raw types, bounds, wildcards, and type erasure in that order.

## Common Mistakes [[Mistakes Log#Generics]]

- Thinking generic types with related type arguments are automatically related
- Mixing up type parameters and type arguments
- Treating `? extends T` as a write-friendly type
- Treating `? super T` as a read-friendly type
- Thinking type erasure creates runtime versions of each generic type
