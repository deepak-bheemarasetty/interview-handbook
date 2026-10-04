## Overview

Production readiness means making behavior observable and safely configurable. Logs answer what happened; metrics show trends; health checks tell orchestrators whether to route traffic or restart an instance.

## Essentials

- Use structured, contextual logs; never log secrets or sensitive customer data.
- Spring Boot Actuator can expose health, metrics, and diagnostic endpoints. Secure and selectively expose them.
- Liveness signals whether a process should be restarted; readiness signals whether it should receive traffic.
- Investigate slow APIs with request metrics, traces, database query timing/plans, pool saturation, and downstream latency before optimizing.

## Interview Takeaway

Start performance troubleshooting from evidence: locate whether time is spent in the application, database, connection pool, or a downstream service. Add measurements before guessing.

```table-of-contents
```
