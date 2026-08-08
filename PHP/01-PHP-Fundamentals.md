# PHP Fundamentals — 0 to 5 YOE

## 1. Runtime model

PHP is a server-side scripting language. A request is handled by a PHP runtime (commonly PHP-FPM behind Nginx/Apache). Source is parsed, compiled to opcodes and executed by the Zend Engine. OPcache can cache compiled bytecode between requests.

### Know for interviews
- CLI vs web SAPI.
- PHP-FPM workers and request lifecycle.
- `php.ini`, extensions, configuration precedence.
- OPcache and why production deployments restart/reload workers.
- PHP 8.x language evolution and backwards compatibility.

## 2. Variables and types

PHP variables use `$name`. PHP is dynamically typed, but modern PHP supports strong type declarations and strict mode.

Core types: `null`, `bool`, `int`, `float`, `string`, `array`, `object`, `resource`, `callable`, plus special pseudo-types such as `mixed`, `void`, `never`, `iterable`, union/intersection types and class/interface types.

```php
<?php
declare(strict_types=1);

function total(int $a, int $b): int {
    return $a + $b;
}
```

### Type conversion
Know implicit coercion, explicit casts, numeric strings, booleans, `null`, arrays and objects. Never assume `==` and `===` behave the same.

## 3. Operators

Arithmetic: `+ - * / % **`  
Comparison: `== === != !== <=> < > <= >=`  
Logical: `&& || ! xor`  
Null: `??`, `??=`  
String: `.` and `.=`  
Array: union `+`, equality and identity operators.

### Interview trap
Prefer strict comparison when type matters:

```php
0 == "0";   // true in typical PHP comparison rules
0 === "0";  // false
```

Do not memorize isolated coercion trivia; understand the comparison tables for the PHP version used by the project.

## 4. Strings

Know single vs double quotes, interpolation, concatenation, heredoc/nowdoc, escaping, common string functions, encoding concerns and UTF-8. `strlen()` measures bytes, not Unicode characters; understand `mb_*` for multibyte text.

## 5. Arrays

PHP arrays are ordered maps. They can act as lists, associative maps and mixed structures.

Know:
- indexed/associative arrays
- `foreach`
- destructuring
- `array_map`, `array_filter`, `array_reduce`
- `array_merge` vs `+`
- references and `foreach` pitfalls
- `isset`, `array_key_exists`
- sorting functions and their key-preserving behaviour
- spread/unpacking

Example:

```php
foreach ($items as &$item) {
    $item['active'] = true;
}
unset($item); // avoid accidental reuse of the reference
```

## 6. Control flow

`if`, `elseif`, `else`, `switch`, `match`, `while`, `do...while`, `for`, `foreach`, `break`, `continue`.

Know that `match` is expression-oriented, uses strict comparison semantics and must handle an unmatched case unless a default exists.

## 7. Functions

Know parameter/return types, default parameters, variadics, named arguments, closures, arrow functions, first-class callables, scope and recursion.

```php
$double = fn(int $n): int => $n * 2;
```

Understand pass-by-value vs pass-by-reference and why references should be used deliberately.

## 8. Scope

Global scope, function scope, static locals, closures and object scope. `global` exists but is usually a design smell in application code.

## 9. Superglobals

`$_GET`, `$_POST`, `$_SERVER`, `$_COOKIE`, `$_SESSION`, `$_FILES`, `$_ENV`, `$_REQUEST`, `$GLOBALS`.

Know that request data is untrusted input. Validate and authorize it; do not trust client-provided identity, price, role or permissions.

## 10. HTTP basics

Understand request method, URI, headers, body, cookies, status code and content type. PHP applications commonly receive HTTP requests through a web server and PHP-FPM.

## 11. Forms, sessions and cookies

Know session identifiers, cookie attributes (`Secure`, `HttpOnly`, `SameSite`), session fixation prevention, CSRF protection and server-side session storage.

## 12. Files and JSON

Know `fopen`, `fread`, `file_get_contents`, `file_put_contents`, streams, JSON encode/decode, error handling and safe path handling. Never concatenate untrusted paths without validation.

## 13. Exceptions and errors

Know `Throwable`, `Error`, `Exception`, custom exceptions, `try/catch/finally`, rethrowing, error handlers and logging. Do not expose stack traces or secrets to production users.

## 14. Date/time

Prefer `DateTimeImmutable` where practical. Understand timezone, parsing, formatting, intervals and DST. Store timestamps consistently and convert at presentation boundaries.

## 15. Security fundamentals

Know XSS, CSRF, SQL injection, command injection, path traversal, unsafe deserialization, SSRF, session attacks, insecure file uploads and secret leakage. Use framework/database parameterization and output encoding rather than hand-built escaping.

## 16. JSON/API work

Know `json_encode`, `json_decode`, associative mode, exceptions/options, malformed JSON handling and content negotiation. Validate schemas at API boundaries.

## 17. Performance fundamentals

Know algorithmic complexity, avoiding unnecessary copies, generators, streaming, database query count, OPcache, caching and profiling. Do not optimize before measuring.

## 18. Generators and iterables

Generators use `yield` to produce values lazily, useful for large datasets/streams where loading everything into memory is undesirable.

## 19. Composer and autoloading overview

Composer manages PHP dependencies and PSR-4 autoloading. Understand `composer.json`, lock files, version constraints, `install` vs `update`, autoload generation and production installation.

## Interview questions — fundamentals

### 0–2 YOE
1. What is PHP and how does a web request reach PHP-FPM?
2. Difference between `==` and `===`?
3. Difference between `isset()` and `empty()`?
4. What are PHP scalar types?
5. What is an associative array?
6. How does `foreach` work?
7. Difference between `include`, `require`, `include_once`, `require_once`?
8. What is a closure?
9. What is variable scope?
10. What are superglobals?
11. GET vs POST?
12. Cookie vs session?
13. What is JSON?
14. How do you handle exceptions?
15. What is type casting?
16. What does `declare(strict_types=1)` do?
17. What is a generator?
18. What is Composer?
19. What is PSR-4?
20. How do you prevent SQL injection?

### 2–3 YOE
21. Explain PHP request lifecycle.
22. Explain PHP-FPM workers.
23. What is OPcache?
24. Explain `array_merge()` vs array union.
25. Explain references and common `foreach` bugs.
26. `isset()` vs `array_key_exists()`?
27. What is late static binding? (covered in OOP chapter)
28. How do closures capture variables?
29. When would you use a generator?
30. How do sessions scale across multiple servers?
31. How would you process a 2 GB file?
32. How do you safely handle file uploads?
33. How would you validate an API request?
34. How do you structure exception handling in a service?
35. What belongs in logs?

### 3–5 YOE
36. Explain PHP memory management at a practical level.
37. What creates memory pressure in long-running workers?
38. How would you diagnose a slow PHP endpoint?
39. How would you find a memory leak-like growth in a worker process?
40. How does OPcache affect deployment?
41. How do you design reusable PHP libraries?
42. How do PSR standards help teams?
43. How would you stream a huge CSV response?
44. How would you safely deserialize untrusted input?
45. How do you design exception boundaries in a REST API?
46. How would you make a PHP job idempotent?
47. How do you protect secrets in a PHP application?
48. What would you check in a production PHP outage?
49. How do you balance validation, domain rules and persistence?
50. What PHP language features have you adopted in modern PHP and why?

## Machine-round practice

1. Implement frequency counting for an array.
2. Find first non-repeating character.
3. Remove duplicates while preserving order.
4. Group records by a field.
5. Implement pagination over an array.
6. Flatten a nested array.
7. Find top K frequent values.
8. Merge overlapping intervals.
9. Implement a simple LRU cache.
10. Write a CSV streaming reader using generators.
11. Validate a nested request payload.
12. Build a simple rate limiter in memory.
13. Implement retry with exponential backoff.
14. Parse and normalize a URL.
15. Write a safe file-upload validation routine.
16. Build a log aggregation script.
17. Implement a simple dependency container.
18. Create a JSON API response helper.
19. Implement idempotency-key handling conceptually.
20. Diagnose and refactor an N+1 database access pattern.

## Mastery checklist

- [ ] Types and coercion understood, not memorized.
- [ ] Arrays and callbacks are comfortable.
- [ ] Functions/closures/references are clear.
- [ ] HTTP/session/cookie fundamentals are clear.
- [ ] Exceptions and logging are production-ready.
- [ ] JSON/file handling is safe.
- [ ] Security basics are understood.
- [ ] Composer/PSR/autoloading are understood.
- [ ] Can solve at least 15 machine-round exercises without copying.
- [ ] Can explain every answer aloud in an interview.
