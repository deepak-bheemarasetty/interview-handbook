## Overview

REST APIs expose resources through HTTP with clear representations, status codes, and stateless requests. Controllers should translate HTTP concerns into application calls, not hold core business logic.

## Request Flow

Use DTOs at the API boundary instead of exposing persistence entities directly. Validate input with Bean Validation (`@Valid`, `@NotBlank`, etc.), map to domain/application types, then return an explicit response DTO.

## Status Code Basics

| Situation | Status |
|---|---:|
| Successful read/update | `200 OK` |
| New resource created | `201 Created` |
| Successful delete with no body | `204 No Content` |
| Invalid client input | `400 Bad Request` |
| Missing resource | `404 Not Found` |
| Conflict such as version violation | `409 Conflict` |
| Unexpected server failure | `500 Internal Server Error` |

Use `@ControllerAdvice` to map known exceptions to a consistent error response. Do not expose stack traces or internal implementation detail to clients.

## Interview Takeaway

Keep controllers thin, validate DTOs at the boundary, and centralize error mapping. A `500` is not a substitute for modeling expected client errors.

```table-of-contents
```
