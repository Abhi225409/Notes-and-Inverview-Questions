# Backend System Design — 3 to 5 YOE

## Interview framework

1. Clarify functional requirements.
2. Clarify non-functional requirements.
3. Estimate traffic/storage.
4. Define APIs and core entities.
5. Design high-level architecture.
6. Choose database and data model.
7. Add caching/queues where justified.
8. Discuss consistency and failure modes.
9. Discuss scaling and bottlenecks.
10. Add security, observability and operational concerns.

## Core concepts

### Scalability
Vertical scaling increases machine capacity; horizontal scaling adds instances. Stateless application servers are easier to scale horizontally.

### Load balancing
Distribute traffic across healthy instances. Understand health checks, connection handling, sticky sessions and failure behaviour.

### Caching
Cache-aside, write-through/write-back concepts, TTL, invalidation, hot keys, stampede protection and distributed cache consistency.

### Databases
Relational DBs are strong for transactional consistency and relational queries. NoSQL systems can be useful for specific access patterns and scale requirements. Choose from requirements, not hype.

### Queues
Decouple producers and consumers, absorb bursts and enable asynchronous work. Know visibility timeout/acknowledgement concepts, retries, dead-letter queues and idempotent consumers.

### Consistency
Understand strong vs eventual consistency, read-after-write, optimistic concurrency and conflict resolution.

### Reliability
Timeouts, retries with backoff, circuit breakers, bulkheads, graceful degradation, health checks, replication, backups and disaster recovery.

### Observability
Logs, metrics, traces, dashboards, alerts, correlation IDs, latency percentiles and error rates.

## Estimation

Know rough calculations for requests/second, storage/day, bandwidth and cache size. State assumptions and keep estimates order-of-magnitude accurate.

## Common designs

### URL shortener
API → app servers → database/cache → redirect path. Use unique key generation, caching of hot URLs, abuse controls and expiration if required.

### Notification system
API → durable queue → worker pool → provider adapters → delivery status store. Make sends idempotent and retryable.

### Payment/order system
Order service → transaction DB → payment provider adapter → webhook processor → reconciliation job. Avoid distributed transactions across your DB and provider; use explicit states and reconciliation.

### File upload/export
Object storage for files; async queue for expensive transformations/export generation; signed URLs for controlled access.

## Interview questions

1. Vertical vs horizontal scaling?
2. Why stateless services?
3. Cache-aside?
4. Cache invalidation strategies?
5. What is cache stampede?
6. What is a hot key?
7. SQL vs NoSQL decision?
8. What is eventual consistency?
9. How do queues improve reliability?
10. What is a dead-letter queue?
11. How do you make consumers idempotent?
12. Retry vs timeout?
13. Why exponential backoff?
14. Circuit breaker?
15. How do you handle DB failure?
16. Read replicas trade-offs?
17. Sharding vs replication?
18. How do you avoid a single point of failure?
19. What are p95/p99 latency?
20. How do you design observability?
21. Design URL shortener.
22. Design notification service.
23. Design payment processing.
24. Design hotel availability search.
25. Design webhook processing.
26. Design rate limiter.
27. Design file upload service.
28. Design job scheduler.
29. Design API gateway.
30. Design audit logging.

## Machine-round/design exercises

1. Design a rate limiter.
2. Design an idempotency service.
3. Design an order service.
4. Design payment webhook processing.
5. Design third-party API reconciliation.
6. Design queue-backed email system.
7. Design URL shortener.
8. Design image processing pipeline.
9. Design large CSV export.
10. Design notification preferences.
11. Design distributed locking strategy.
12. Design audit log pipeline.
13. Design metrics ingestion.
14. Design API throttling.
15. Design multi-tenant backend.

## Mastery checklist

- [ ] Can clarify ambiguous requirements.
- [ ] Can estimate traffic and storage.
- [ ] Can model APIs/entities.
- [ ] Can justify DB/cache/queue choices.
- [ ] Can discuss failures and consistency.
- [ ] Can identify bottlenecks and scaling strategies.
- [ ] Can explain security and observability.
