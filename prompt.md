I am preparing for [Level] full-stack engineering interviews (targeting FAANG+ and high-growth startups).I need a comprehensive set of [Number] real-world problem-solving scenarios that test:

1. **Critical Thinking** - Trade-off analysis, risk assessment, and decision-making under constraints
2. **Algorithmic Thinking** - Efficiency, scalability, and data structure selection in production contexts
3. **System Design Judgment** - Architecture decisions, failure modes, and operational excellence

## Please structure each scenario as:

- **Context**: The business/technical situation (1-2 sentences)
- **The Problem**: A specific challenge with constraints (deadlines, scale, legacy code, team size, etc.)
- **Guiding Questions**: 2-3 probing questions that force me to think through options
- **Expected Depth**: What a strong answer should cover (trade-offs, implementation details, monitoring, rollback plans)

## Core Domains to Cover (distribute roughly equally):

| Domain                          | Specific Topics                                                                                                                                                 |
| ------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Databases**                   | Schema migrations (zero-downtime), indexing strategies, deadlocks, replication lag, sharding, eventual consistency, transaction isolation, foreign key dilemmas |
| **Caching**                     | Cache invalidation strategies, write-through vs write-behind, cache stampede, TTL tuning, multi-tier caching, cache warming                                     |
| **System Design**               | Rate limiting, retry with backoff, circuit breakers, idempotency, event-driven vs request-response, API versioning, graceful degradation                        |
| **Frontend (React/Next)**       | State management complexity, render optimization, code splitting, SSR/SSG trade-offs, Web Vitals, real-time updates, form handling at scale                     |
| **Backend (Node/Express/Nest)** | Request lifecycle optimization, middleware ordering, error handling patterns, dependency injection, microservices communication, background jobs                |
| **DevOps/Production**           | CI/CD pipeline failures, feature flags, canary deployments, logging strategy, monitoring alerts, incident response                                              |
| **Integration**                 | Third-party API failures, webhook reliability, data sync between services, OAuth flows, file uploads at scale                                                   |
| **Security**                    | SQL injection prevention, XSS, CSRF, rate limiting abuse, JWT management, environment variable security                                                         |

## Additional Requirements:

- Mix difficulty levels: 20% easy (junior), 50% medium (mid-level), 30% hard (senior/architect)
- Include at least 5 scenarios where the "right" answer is "do nothing" or "it depends"
- Make [Number] scenarios specific to e-commerce, [Number] to SaaS, [Number] to fintech, [Number] to social media, [Number] to general enterprise
- For each scenario, note which interview round it's best suited for (coding, system design, or behavioral)

## Example Scenario Format:

---

## Scenario #1\*\* (Medium | System Design Round | E-commerce)

### Context:

You're the lead engineer on a high-traffic e-commerce platform. The product team wants to add a new discount_eligible boolean column to the orders table. The column must never be null for new orders, but historical orders have no value.

### Problem:

Deploy this change to a production database with 10M+ orders, 5000+ concurrent writes/min, zero downtime, and no data corruption.

### Guiding Questions\*\*:

1. How would you handle the backfill of 10M records without locking the table?
2. What would your migration script look like? How would you deploy it?
3. How would you validate that the migration succeeded without incident?

### Strong Answer Should Include:

- Phased rollout with dual-write pattern
- Using online schema change tools (gh-ost, pt-online-schema-change)
- Backfill strategy with batched updates and throttle control
- Rollback plan and monitoring during migration
- Handling application logic to treat NULL as false during the transition

---

**Now generate [Number] such scenarios following this exact structure. Prioritize realism over textbook answers—situations where production constraints force imperfect but pragmatic solutions.**
