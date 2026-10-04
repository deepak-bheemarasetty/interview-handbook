## Overview

The Spring container creates, configures, and wires application objects called beans. Inversion of Control means the container, rather than business code, controls this construction lifecycle.

## Dependency Injection

Constructor injection makes required dependencies explicit, supports immutable fields, and simplifies unit tests. With one constructor, `@Autowired` is optional in modern Spring.

```java
@Service
class OrderService {
    private final OrderRepository repository;
    OrderService(OrderRepository repository) { this.repository = repository; }
}
```

## Stereotypes and Scopes

`@Component` is a general discovered bean; `@Service`, `@Repository`, and `@Controller` communicate roles. `@RestController` combines controller behavior with response-body serialization. Singleton is the default scope; a singleton must not store per-request mutable state. Other scopes include prototype, request, and session.

## Lifecycle

Spring instantiates a bean, injects dependencies, runs initialization callbacks, and later runs destruction callbacks for managed beans. Avoid expensive work or external side effects during construction.

## Interview Takeaway

Use constructor injection for required dependencies. The container manages object graph and lifecycle, making code easier to test and implementations easier to swap.

```table-of-contents
```
