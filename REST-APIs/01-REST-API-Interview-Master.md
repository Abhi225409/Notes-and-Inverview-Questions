# REST APIs — Interview Master

## HTTP fundamentals

Know methods GET, POST, PUT, PATCH, DELETE, HEAD, OPTIONS; safe vs idempotent semantics; status codes; headers; content types; caching and conditional requests.

### Status codes

2xx success, 3xx redirection, 4xx client-side/request problems, 5xx server-side failures. Be precise: 400 malformed/invalid request, 401 unauthenticated, 403 authenticated but forbidden, 404 resource not found, 409 conflict, 422 semantic validation commonly used by APIs, 429 rate limited, 500 server failure, 502/503/504 often indicate upstream/gateway/service availability problems.

## Resource design

Use nouns/resources, consistent URLs, predictable representations, pagination/filtering/sorting, stable identifiers and explicit error formats.

## Authentication

Understand sessions, API keys, bearer tokens, OAuth 2.0 concepts, JWT trade-offs, refresh tokens, scopes, token expiration and secret storage. Authentication answers who you are; authorization answers what you can do.

## Idempotency

An operation is idempotent when repeating it has the same intended effect. PUT/DELETE have defined idempotency semantics; POST usually does not. For payments/order creation, use an idempotency key persisted with the request/result.

## Validation and errors

Validate at boundaries. Return machine-readable error codes/messages and correlation/request IDs. Do not leak stack traces or secrets.

## Pagination

Offset pagination is simple but can become slow/unstable under changing datasets. Cursor/keyset pagination is often better for large, frequently changing data.

## Rate limiting

Understand fixed/sliding windows, token bucket, distributed counters and `Retry-After`. Rate limits should protect expensive resources and be observable.

## Caching

Know HTTP cache headers, ETag/If-None-Match, Cache-Control and application-level caching. Invalidation and correctness matter more than adding a cache blindly.

## Webhooks

Verify signatures, validate timestamp/replay windows where applicable, persist the event, acknowledge quickly, process asynchronously, make handling idempotent and provide reconciliation/retry paths.

## Resilience

Use timeouts, bounded retries, exponential backoff with jitter, circuit breaking where appropriate, bulkheads and clear failure semantics. Never retry non-idempotent operations blindly.

## Security

HTTPS, input validation, authorization, least privilege, secret management, SSRF protection, request-size limits, secure file handling, audit logs and dependency patching.

## Interview questions

1. REST vs SOAP?
2. GET vs POST?
3. PUT vs PATCH?
4. What is idempotency?
5. 401 vs 403?
6. 400 vs 422?
7. 409 use case?
8. How would you version APIs?
9. Offset vs cursor pagination?
10. JWT pros/cons?
11. OAuth2 flow overview?
12. How do refresh tokens work?
13. How do you secure webhooks?
14. How do you prevent duplicate webhook processing?
15. How do you retry third-party calls?
16. Why use timeouts?
17. What is exponential backoff?
18. Why add jitter?
19. What is rate limiting?
20. How do you design consistent API errors?
21. How do ETags work?
22. How do you handle large file uploads?
23. How do you protect against SSRF?
24. How do you handle API deprecation?
25. How do you trace requests across services?
26. What is correlation ID?
27. How do you design an API for a payment provider?
28. How do you reconcile webhook vs API state?
29. How do you handle upstream outages?
30. How would you review an API for security?

## Machine-round exercises

1. Design CRUD API.
2. Add pagination/filter/sort.
3. Implement idempotency keys.
4. Build webhook endpoint with signature verification.
5. Build retrying HTTP client.
6. Add rate limiter.
7. Design API versioning.
8. Design file upload API.
9. Design asynchronous export API.
10. Design order creation with duplicate protection.
11. Design payment status API.
12. Design provider reconciliation API.
13. Design API error envelope.
14. Design request tracing.
15. Design cursor pagination.
