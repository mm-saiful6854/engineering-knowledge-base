# Design Patterns

Design patterns are reusable ways to solve common software design problems. They are not rules; they are vocabulary for discussing tradeoffs.

## Why It Matters

Patterns help engineers recognize familiar problems and communicate solutions quickly. They are most useful when they reduce complexity rather than add ceremony.

## Pattern Map

| Pattern | Category | Use when |
| --- | --- | --- |
| Strategy | Behavioral | You need interchangeable algorithms or policies. |
| Decorator | Structural | You need to add behavior without changing the original object. |
| Observer | Behavioral | Many listeners need to react to events. |
| Singleton | Creational | Exactly one shared instance is truly required. |
| Object Pool | Creational | Objects are expensive to create and reused frequently. |
| Circuit Breaker | Resilience | A failing remote dependency should not take down the system. |
| Queue-Based Load Leveling | Concurrency | Producers can tolerate delayed processing through a queue. |
| [Command](command.md) | Behavioral | A request should be represented as an object. |
| [CQRS](cqrs.md) | Architectural | Read and write models need different structures. |
| [Transaction Idempotency](transaction-idempotency.md) | Reliability | Retried operations must not duplicate side effects. |

## Common Mistakes

- Adding patterns before the problem needs them.
- Memorizing pattern names without understanding tradeoffs.
- Treating Singleton as a default global state mechanism.
- Ignoring simpler language features that already solve the problem.

## Related Topics

- [Object-Oriented Programming](../oop.md)
- [System Design Foundations](../foundations.md)
