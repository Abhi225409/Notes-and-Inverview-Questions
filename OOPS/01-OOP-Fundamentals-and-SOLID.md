# OOP & SOLID — PHP Interview Master Notes

## Core model

Object-oriented programming models software around objects that combine state and behaviour. In PHP, classes define objects, interfaces define contracts, and traits provide reusable implementation.

## Four classic principles

### Encapsulation
Hide implementation details behind a stable public API. Use visibility (`public`, `protected`, `private`) and methods that enforce invariants.

### Abstraction
Expose what a component does rather than how it does it. Interfaces and abstract classes are common tools.

### Inheritance
A class can extend another class. Use inheritance for genuine substitutability, not merely code reuse.

### Polymorphism
Different implementations can satisfy the same contract and be used through the common type.

## Composition vs inheritance

Prefer composition when behaviour varies independently. A service depending on a `PaymentGateway` interface is more replaceable than a deep inheritance hierarchy.

## Interface vs abstract class

An interface expresses a contract and supports multiple interface implementations. An abstract class can share state and implementation while requiring subclasses to implement abstract members.

## Traits

Traits compose method/property implementations into classes. They are useful for focused reusable behaviour but can hide dependencies if overused.

## Visibility, static and readonly

Know `public`, `protected`, `private`, `static`, constructors, promoted properties, readonly properties/classes where supported by the project PHP version, and typed properties.

## Constructor injection

Inject dependencies explicitly:

```php
final class OrderService
{
    public function __construct(private PaymentGateway $gateway) {}
}
```

This improves testing, readability and dependency management.

## SOLID

### S — Single Responsibility Principle
A class should have one coherent reason to change. Avoid god services that validate, calculate, persist, email and call external APIs all at once.

### O — Open/Closed Principle
Prefer extension through contracts/composition rather than modifying stable code for every new variant.

### L — Liskov Substitution Principle
Subtypes should be usable wherever the base abstraction is expected without breaking behavioural expectations.

### I — Interface Segregation Principle
Prefer small client-specific interfaces over huge interfaces that force unused methods on consumers.

### D — Dependency Inversion Principle
High-level policy should depend on abstractions rather than concrete infrastructure.

## Design patterns worth knowing

- Strategy
- Factory Method / Factory
- Adapter
- Decorator
- Observer / Event Listener
- Command
- Repository (and its trade-offs)
- Builder
- Template Method
- Chain of Responsibility
- Singleton and why it often harms testability

## PHP-specific interview areas

- `self` vs `static` vs `parent`
- late static binding
- method/property visibility
- final classes/methods
- covariance and contravariance
- typed properties
- union/intersection types
- anonymous classes
- magic methods and why they should be used carefully
- cloning and `__clone`
- object identity vs value equality
- serialization concerns

## Interview questions

1. Explain encapsulation with a real example.
2. Interface vs abstract class?
3. Composition vs inheritance?
4. Explain polymorphism in PHP.
5. What is dependency inversion?
6. Explain all SOLID principles with examples.
7. What is a trait and when would you avoid one?
8. What is late static binding?
9. `self` vs `static`?
10. What is method overriding?
11. What are covariant return types?
12. What is contravariance?
13. Why prefer constructor injection?
14. What is a value object?
15. Entity vs value object?
16. What makes a class immutable?
17. What is a god object?
18. What is tight coupling?
19. Why can Singleton be problematic?
20. Strategy vs Factory?
21. Adapter vs Decorator?
22. Repository pattern: benefits and drawbacks?
23. How would you refactor a 1000-line service?
24. How would you design multiple payment providers?
25. How would you make a notification system extensible?
26. How would you test a class with an external API dependency?
27. How would you apply SOLID to Laravel services?
28. What is dependency injection?
29. DI vs service locator?
30. How do you identify a violation of SRP?

## Machine-round exercises

1. Design a payment gateway abstraction with Stripe/PayPal-like adapters.
2. Implement Strategy for multiple pricing algorithms.
3. Implement a Factory for provider selection.
4. Implement a Decorator for API logging.
5. Build a notification dispatcher using interfaces.
6. Refactor a god class into cohesive services.
7. Model an Order aggregate and enforce invariants.
8. Create a value object for Money.
9. Design a pluggable file-storage abstraction.
10. Write unit tests using dependency injection and mocks/fakes.
11. Implement Chain of Responsibility for validation rules.
12. Design a cache abstraction with two implementations.
13. Design a retry policy using Strategy.
14. Explain where SOLID should *not* be over-applied.
15. Review a code sample and list coupling/design smells.

## Mastery checklist

- [ ] Can explain each SOLID principle with a production example.
- [ ] Can choose composition over inheritance appropriately.
- [ ] Can design interfaces from consumer needs.
- [ ] Can explain PHP-specific OOP behaviour.
- [ ] Can refactor procedural/god-class code.
- [ ] Can implement Strategy, Factory, Adapter and Decorator without notes.
