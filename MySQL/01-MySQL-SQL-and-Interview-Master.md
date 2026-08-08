# MySQL — SQL, Internals & Interview Master

## SQL foundations

Know databases, schemas, tables, rows, columns, primary keys, foreign keys, unique constraints, nullability, defaults and data types.

CRUD: `SELECT`, `INSERT`, `UPDATE`, `DELETE`.

## Query execution mindset

For every query understand:
1. What rows are needed?
2. Which predicates can reduce rows early?
3. Which indexes can support filtering/join/order?
4. How many rows are estimated and actually scanned?
5. Does the result require sorting/grouping/temp work?

Use `EXPLAIN` and, where available, `EXPLAIN ANALYZE` to investigate rather than guessing.

## Joins

Understand INNER, LEFT, RIGHT and CROSS joins, join predicates, duplicate rows from one-to-many relationships and anti-joins (`NOT EXISTS` / `LEFT JOIN ... IS NULL`).

## Aggregation

`GROUP BY`, aggregate functions, `HAVING`, conditional aggregation and grouping at the correct grain.

## Subqueries and CTEs

Know correlated vs non-correlated subqueries, `EXISTS`, `NOT EXISTS`, derived tables and CTEs. Use window functions when you need row-level data alongside group calculations.

## Window functions

Know `ROW_NUMBER`, `RANK`, `DENSE_RANK`, `LAG`, `LEAD`, partitioning and ordering. Typical interview problem: top N per group.

## Indexes

An index is a data structure that helps locate rows efficiently. Understand:
- single-column indexes
- composite indexes
- leftmost-prefix behaviour for composite indexes
- selectivity/cardinality
- covering indexes
- index-only access where applicable
- why excessive indexes slow writes
- why functions/casts on indexed columns can prevent efficient use depending on expression/index support

Design indexes from real query patterns, not from every column.

## Transactions

A transaction groups operations into an atomic unit. Know `COMMIT`, `ROLLBACK`, savepoints and the ACID properties.

### Isolation
Understand dirty reads, non-repeatable reads, phantom reads and the trade-offs among isolation levels. Know the default isolation level of the MySQL/InnoDB version used by the project rather than assuming it never changes.

## InnoDB concepts

Know clustered primary-key storage, secondary indexes, row-level locking, MVCC, undo/redo concepts and foreign-key enforcement at a practical level.

## Locks and concurrency

Understand shared/exclusive locks, deadlocks, lock waits and consistent transaction ordering. A deadlock is normally resolved by rolling back one transaction; application code should make retries safe where appropriate.

## Normalization

Know 1NF/2NF/3NF conceptually, functional dependencies, normalization benefits and deliberate denormalization for performance/reporting.

## Schema design

Choose correct types, enforce constraints in the database, avoid storing multiple values in a single field unless there is a deliberate reason, and model many-to-many relationships with junction tables.

## NULL

`NULL` means unknown/absent, not zero or empty string. Use `IS NULL`/`IS NOT NULL`; comparisons such as `column = NULL` do not work as expected.

## SQL injection

Never concatenate untrusted values into SQL. Use parameterized queries/prepared statements and safe query-builder APIs.

## Performance checklist

- inspect query plan
- verify indexes
- reduce selected columns
- reduce row count early
- avoid accidental Cartesian products
- avoid N+1 queries
- paginate deliberately
- measure before/after
- inspect locks and slow-query logs

## Interview questions

1. Primary key vs unique key?
2. WHERE vs HAVING?
3. INNER vs LEFT JOIN?
4. What causes duplicate rows after a join?
5. `COUNT(*)` vs `COUNT(column)`?
6. What is an index?
7. Why not index every column?
8. Composite index and leftmost prefix?
9. What is a covering index?
10. Explain ACID.
11. What is a transaction?
12. Explain isolation levels.
13. Dirty/non-repeatable/phantom reads?
14. What is MVCC?
15. What is a deadlock?
16. How do you debug a deadlock?
17. `DELETE` vs `TRUNCATE` vs `DROP`?
18. `UNION` vs `UNION ALL`?
19. `EXISTS` vs `IN`?
20. Correlated subquery?
21. CTE vs subquery?
22. What is a window function?
23. Find second-highest salary.
24. Find duplicate records.
25. Find top 3 salaries per department.
26. Find customers with no orders.
27. Find latest row per customer.
28. Calculate running total.
29. Find consecutive records/dates.
30. How would you optimize a slow query?
31. Why can an index be ignored?
32. What is selectivity?
33. What is normalization?
34. When would you denormalize?
35. Explain clustered vs secondary index conceptually in InnoDB.
36. Why can long transactions be dangerous?
37. How do you prevent overselling inventory?
38. How do you make a financial update atomic?
39. How would you migrate a huge table safely?
40. How would you handle millions of rows in pagination?

## Machine-round SQL set

1. Second-highest salary.
2. Nth-highest salary.
3. Top 3 per department.
4. Duplicate email detection.
5. Delete duplicate records while preserving one row.
6. Customers with no orders.
7. Orders in last 30 days.
8. Monthly revenue.
9. Running monthly revenue.
10. Month-over-month growth.
11. Latest order per customer.
12. First order per customer.
13. Repeat customers.
14. Products never sold.
15. Most popular product per category.
16. Detect gaps in sequential IDs conceptually.
17. Consecutive login days.
18. 7-day rolling average.
19. Rank employees within department.
20. Find overlapping date ranges.
21. Inventory decrement transaction.
22. Seat reservation transaction.
23. Wallet debit/credit transaction.
24. Deadlock-prone transfer and safe ordering.
25. Index design for a provided query.
26. Explain a supplied `EXPLAIN` plan.
27. Rewrite an N+1 access pattern.
28. Paginate large result sets.
29. Archive old records.
30. Safe zero-downtime schema migration strategy.

## Mastery checklist

- [ ] Can write joins without trial-and-error.
- [ ] Can solve window-function problems.
- [ ] Can design composite indexes from query patterns.
- [ ] Can explain transactions and isolation.
- [ ] Can read an execution plan.
- [ ] Can diagnose N+1 and slow queries.
- [ ] Can design safe concurrent updates.
- [ ] Can solve at least 25 machine-round SQL problems.
