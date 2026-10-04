## Overview

Object-oriented programming organizes software around objects that combine state and behavior. The aim is to model responsibilities clearly and keep change localized.

## Four Pillars

| Concept | Meaning | Interview example |
|---|---|---|
| Encapsulation | Hide representation behind a small API | `balance` is private; `deposit()` validates changes |
| Abstraction | Expose what a caller needs, hide how it works | `PaymentGateway.charge()` hides provider details |
| Inheritance | Reuse or specialize an is-a relationship | `SavingsAccount extends Account` |
| Polymorphism | Use one interface with multiple implementations | `List` may be an `ArrayList` or `LinkedList` |

## Composition vs Inheritance

Prefer composition when a class **has a** collaborator and behavior may vary. For example, `OrderService` receives a `PaymentGateway`. Use inheritance only for a stable, genuine **is a** relationship that preserves substitutability. Composition avoids tight coupling to a superclass and makes testing easier.

## SOLID Basics

| Principle | Practical reading |
|---|---|
| Single Responsibility | One reason to change; split validation, persistence, and notification concerns |
| Open/Closed | Add a new strategy/implementation instead of repeatedly editing conditionals |
| Liskov Substitution | A subtype must work wherever its base type is expected |
| Interface Segregation | Prefer small, client-specific interfaces over one large interface |
| Dependency Inversion | Depend on abstractions; inject infrastructure implementations |

## Interview Takeaway

Say that OOP is not about maximizing inheritance. Use encapsulation to protect invariants, interfaces and polymorphism for variation, and composition by default for flexible design.

## Common Mistakes [[Mistakes Log#OOP]]

- Calling every use of a class abstraction
- Using inheritance merely to reuse code
- Treating a getter/setter for every field as meaningful encapsulation

```table-of-contents
```
