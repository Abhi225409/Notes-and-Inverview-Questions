# Laravel — 0 to 5 YOE Interview Master

## Architecture

Understand Laravel's HTTP request flow: web server → PHP runtime → framework bootstrap → service providers/container → middleware → router/controller → application services → persistence/external systems → response.

Know MVC, service container, service providers, facades, contracts, middleware, events and queues.

## Routing and middleware

Know route parameters, named routes, route model binding, groups, middleware order, authentication middleware, throttling and API/web middleware differences.

## Dependency Injection / Service Container

The container resolves dependencies and supports bindings, contextual bindings and lifecycle scopes. Prefer constructor injection for explicit dependencies.

Interview focus: singleton binding vs transient resolution, interface-to-implementation binding, circular dependencies and testing with mocks/fakes.

## Service providers

Providers are the framework mechanism for registering bindings/configuration and bootstrapping services. Know `register` vs `boot` and why heavy work should not happen during bootstrap.

## Controllers and validation

Controllers should coordinate request/response concerns rather than become giant business-logic classes. Use Form Requests for reusable validation/authorization rules when appropriate.

Know validation rules, custom rules, authorization, nested arrays, conditional validation and consistent API error responses.

## Eloquent

Know models, mass assignment, `$fillable`/`$guarded`, casts, accessors/mutators, scopes, relationships and eager loading.

Relationships: one-to-one, one-to-many, many-to-many, polymorphic and through relationships.

### N+1

Avoid lazy-loading relationships inside loops when data can be eager loaded. Use `with`, constrained eager loading and query inspection.

## Query Builder

Know parameter binding, joins, aggregates, subqueries, transactions, chunking/lazy iteration and raw expressions. Raw SQL must still be parameterized safely.

## Transactions

Use transactions for invariants spanning multiple writes. Keep transaction scope short and avoid unnecessary external network calls inside a DB transaction.

## Queues

Know jobs, queue drivers, workers, retries, backoff, failed jobs, timeout, idempotency and serialization. A job can be delivered more than once; design side effects accordingly.

## Events/listeners

Use events for decoupling domain/application reactions. Understand synchronous vs queued listeners and when events can make flow harder to trace.

## Caching

Know cache-aside patterns, TTL, invalidation, cache keys, tags where supported, stampede concerns and distributed cache implications. Never cache sensitive data without deliberate controls.

## Authentication/authorization

Know sessions, API tokens/Sanctum-like approaches, guards/providers, policies, gates, roles/permissions and authorization at the resource/action boundary.

## APIs

Know API Resources, validation, pagination, versioning, status codes, authentication, rate limiting, idempotency and consistent error formats.

## Files, mail and notifications

Know storage disks, signed URLs, queued mail/notifications, file validation and access control.

## Scheduling

Know scheduled commands/jobs, cron invocation, overlap prevention and idempotency.

## Testing

Know unit vs feature tests, factories, seeders, HTTP tests, database transactions/refresh strategies, mocks/fakes, queue/mail/event assertions.

## Security

Understand CSRF, XSS, SQL injection, mass assignment, insecure direct object references, SSRF, file upload risks, secret management, authorization bypass and session security.

## Performance

Measure query count, N+1, indexes, cache usage, queueing, PHP-FPM workers, OPcache and slow external APIs. Use profiling/APM rather than assumptions.

## Production architecture

Be able to explain web/queue workers, load balancer, app servers, MySQL, Redis/cache, object storage, queues, cron/scheduler, logs and monitoring.

## Interview questions — 0–2 YOE

1. Explain Laravel request lifecycle.
2. What is middleware?
3. What is a service provider?
4. What is service container?
5. Facade vs dependency injection?
6. What is route model binding?
7. Form Request vs controller validation?
8. What is Eloquent?
9. Relationship types?
10. What is eager loading?
11. Explain N+1.
12. What are migrations?
13. What are seeders/factories?
14. What is a queue?
15. What is a job?
16. What is a policy?
17. Gate vs policy?
18. What is cache?
19. What are API resources?
20. How does CSRF protection work?

## 2–3 YOE

21. Explain container bindings.
22. Singleton vs normal binding.
23. Explain provider boot/register.
24. How do you optimize N+1?
25. How do you handle transactions?
26. How do queue retries work?
27. How do you make jobs idempotent?
28. How do you design a reusable service class?
29. How do you structure domain/business rules?
30. How do you version an API?
31. How do you implement rate limiting?
32. How do you secure file downloads?
33. How do you handle large imports?
34. Chunk vs cursor/lazy iteration?
35. How do you debug slow Laravel requests?
36. How do you test queued jobs?
37. How do you test external APIs?
38. How do you invalidate cache safely?
39. How do you prevent mass assignment vulnerabilities?
40. How do you handle authorization in APIs?

## 3–5 YOE

41. Design a high-volume Laravel API.
42. Design a queue architecture for 1M jobs/day.
43. How would you scale Laravel horizontally?
44. How do sessions work with multiple app servers?
45. How would you handle cache stampede?
46. How would you guarantee a payment webhook is processed once logically?
47. How would you reconcile DB state with an external API?
48. How would you safely process a 10M-row import?
49. How would you deploy without downtime?
50. How would you diagnose queue backlog?
51. How would you handle deadlocks?
52. How would you design multi-tenant Laravel architecture?
53. How would you separate domain logic from framework code?
54. When should you use events vs direct service calls?
55. How do you avoid a distributed transaction across MySQL and an external API?
56. How do you design resilient third-party integrations?
57. How do you secure internal/admin APIs?
58. How do you handle secrets and configuration across environments?
59. How would you design observability?
60. How would you review a Laravel codebase for production risks?

## Machine-round exercises

1. CRUD API with Form Request validation.
2. Eloquent relationships with eager loading.
3. Fix an N+1 implementation.
4. Import 100k records using chunking/queues.
5. Implement idempotent webhook handling.
6. Implement retryable external API client.
7. Build provider adapter pattern.
8. Add API pagination/filtering/sorting.
9. Add authorization policy.
10. Add cache-aside layer.
11. Implement queued notification.
12. Implement scheduled reconciliation job.
13. Design failed-job recovery.
14. Add transaction around inventory update.
15. Prevent duplicate order creation using idempotency key.
16. Build rate-limited API endpoint.
17. Write tests for an external integration using fakes.
18. Refactor a fat controller.
19. Refactor a god service.
20. Diagnose a slow endpoint from query logs.
21. Design a multi-provider payment interface.
22. Implement safe file upload/download.
23. Build an admin audit log.
24. Design a large CSV export using a queue.
25. Design webhook retry/reconciliation.
26. Build a notification preference system.
27. Implement optimistic/concurrency-safe update.
28. Design a cache invalidation strategy.
29. Create a versioned API.
30. Explain production deployment architecture.

## Mastery checklist

- [ ] Request lifecycle can be drawn from memory.
- [ ] Container/providers/middleware are clear.
- [ ] Eloquent relationships and N+1 are strong.
- [ ] Transactions and queues are production-ready concepts.
- [ ] API/security/testing/performance are strong.
- [ ] Can solve 20+ Laravel machine tasks without copying.
