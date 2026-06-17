# Domain-Driven Design

Domain-Driven Design, or DDD, is an approach to software design that puts the business domain and shared language at the center of the model.

## Why It Matters

Complex systems become hard to change when code structure does not match the business concepts. DDD helps teams align software boundaries with domain boundaries.

## Core Concepts

### Domain

The domain is the problem area the software is built for, such as banking, ecommerce, logistics, or education.

### Ubiquitous Language

Developers and domain experts should use the same vocabulary in conversation, documentation, and code.

### Bounded Context

A bounded context is a boundary where a model and vocabulary have a specific meaning.

Example:

- In billing, "customer" may mean the account that pays.
- In support, "customer" may mean the person asking for help.

Those meanings should not be forced into one universal model if they behave differently.

### Entities and Value Objects

- Entity: has identity over time, such as `Order`.
- Value object: defined by its values, such as `Money` or `Address`.

### Aggregates

An aggregate is a consistency boundary around related objects. One aggregate root controls changes inside that boundary.

## Common Mistakes

- Treating DDD as only folder naming.
- Creating many microservices before understanding bounded contexts.
- Using one database model as the domain model everywhere.
- Ignoring domain experts and inventing technical vocabulary instead.

## Related Topics

- [System Design Foundations](foundations.md)
- [Object-Oriented Programming](oop.md)
- [UML](uml.md)

## References

- Martin Fowler on bounded context: <https://martinfowler.com/bliki/BoundedContext.html>
- Domain-Driven Design reference: <https://domainlanguage.com/ddd/reference/>
