## Overview

Authentication establishes who a caller is; authorization decides what that caller may do. A secure API validates credentials, applies least privilege, and protects each request boundary.

## Core Concepts

- Use Spring Security's filter chain to authenticate requests before controllers run.
- Store passwords with a slow, salted adaptive hash such as bcrypt or Argon2—never reversible encryption or plain text.
- Sessions keep server-side state; signed bearer tokens carry claims and must be validated for signature, expiry, issuer, and audience as appropriate.
- Apply authorization by role/authority and, when needed, ownership or domain-level checks.
- Protect state-changing browser session flows from CSRF; configure CORS deliberately rather than broadly allowing origins.

## Interview Takeaway

Authentication and authorization are separate. Security is layered: secure credentials, validate every request, authorize narrowly, and avoid leaking sensitive data in errors/logs.

```table-of-contents
```
