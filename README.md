# Real-World Full-Stack Engineering Interview Scenarios

## Coverage Summary

| #                  | Topic                                    | Difficulty | Round                    |
| ------------------ | ---------------------------------------- | ---------- | ------------------------ |
| [1](#Scenario-1)   | Zero-downtime DB migration               | Medium     | System Design            |
| [2](#Scenario-2)   | Redis caching                            | Easy       | Coding                   |
| [3](#Scenario-3)   | Distributed inventory consistency        | Hard       | System Design            |
| [4](#Scenario-4)   | Idempotent payment APIs                  | Medium     | Backend                  |
| [5](#Scenario-5)   | React rendering optimization             | Medium     | Frontend                 |
| [6](#Scenario-6)   | Cache TTL trade-offs ("It depends")      | Medium     | Behavioral               |
| [7](#Scenario-7)   | Canary deployment & rollback             | Hard       | System Design            |
| [8](#Scenario-8)   | Third-party API resilience               | Medium     | Backend                  |
| [9](#Scenario-9)   | Premature optimization ("Do nothing")    | Hard       | Behavioral               |
| [10](#Scenario-10) | Secure file uploads                      | Hard       | System Design            |
| [11](#Scenario-11) | Replication lag & read consistency       | Medium     | System Design            |
| [12](#Scenario-12) | Background jobs & queues                 | Medium     | Backend                  |
| [13](#Scenario-13) | Monolith vs microservices ("It depends") | Hard       | Behavioral/System Design |
| [14](#Scenario-14) | JWT storage & authentication             | Easy       | Coding                   |
| [15](#Scenario-15) | Rate limiting                            | Hard       | System Design            |
| [16](#Scenario-16) | React state management                   | Medium     | Frontend                 |
| [17](#Scenario-17) | Database deadlocks                       | Medium     | Backend                  |
| [18](#Scenario-18) | Performance metrics ("Do nothing")       | Medium     | Behavioral               |
| [19](#Scenario-19) | API versioning                           | Hard       | System Design            |
| [20](#Scenario-20) | Event-driven architecture                | Hard       | System Design            |

### Scenario #1

**Difficulty**: Medium
**Interview Round**: System Design
**Domain**: Database (Zero-Downtime Migration)

#### Context

Your e-commerce platform has 15 million orders. Product wants a new discount_eligible field added before Black Friday. The site cannot experience downtime.

#### Problem

The table receives around 7,000 writes/minute. Historical records need a value, but locking the table for several minutes is unacceptable.

#### Guiding Questions

1. How do you deploy the schema safely?
2. How would you backfill millions of rows?
3. How do you verify the migration before removing compatibility code?

#### Hints

[Click here](#Hints-of-Scenario-1)

### Scenario #2

**Difficulty**: Easy
**Interview Round**: Coding + Discussion
**Domain**: Caching

#### Context

The homepage loads featured products from the database every request.

#### Problem

Traffic spikes to 20,000 requests/min during flash sales. Database CPU reaches 95%.

#### Guiding Questions

1. Should you cache?
2. What cache TTL would you choose?
3. How do you invalidate the cache?

#### Hints

[Click here](#Hints-of-Scenario-2)

### Scenario #3

**Difficulty**: Hard
**Interview Round**: System Design
**Domain**: Database + Consistency

#### Context

Inventory is stored in multiple regions.

#### Problem

Two customers in different regions purchase the last item simultaneously.

#### Guiding Questions

1. How do you prevent overselling?
2. Would you choose strong consistency or eventual consistency?
3. What compromises are acceptable?

#### Hints

[Click here](#Hints-of-Scenario-3)

### Scenario #4

**Difficulty**: Medium
**Interview Round**: Backend Design
**Domain**: Retry & Idempotency

#### Context

Payments occasionally timeout after charging the customer's card.

#### Problem

The frontend retries automatically, sometimes charging twice.

#### Guiding Questions

1. How do you make payment requests safe?
2. What should happen if the client retries?
3. What identifiers should be stored?

#### Hints

[Click here](#Hints-of-Scenario-4)

### Scenario #5

**Difficulty**: Medium
**Interview Round**: Frontend
**Domain**: React Performance

#### Context

The product catalog contains 80,000 products.

#### Problem

Scrolling becomes sluggish after implementing several filtering options.

#### Guiding Questions

1. What is causing excessive rendering?
2. How would you optimize the UI?
3. What metrics would you measure?

#### Hints

[Click here](#Hints-of-Scenario-5)

### Scenario #6 (It Depends Scenario #1)

**Difficulty**: Medium
**Interview Round**: Behavioral + System Design
**Domain**: Caching

#### Context

Marketing requests that every product page be cached for one hour.

#### Problem

Prices change multiple times per hour.

#### Guiding Questions

1. Is one-hour caching appropriate?
2. What business risks exist?
3. Would you cache everything?

#### Hints

[Click here](#Hints-of-Scenario-6)

### Scenario #7

**Difficulty**: Hard
**Interview Round**: System Design
**Domain**: DevOps

#### Context

A deployment introduces a hidden checkout bug.

#### Problem

Only 3% of users are affected, but revenue begins dropping.

#### Guiding Questions

1. How would you detect the issue?
2. How would you minimize impact?
3. What deployment strategy helps here?

#### Hints

[Click here](#Hints-of-Scenario-7)

### Scenario #8

**Difficulty**: Medium
**Interview Round**: Backend/System Design
**Domain**: Third-Party Integration

#### Context

Shipping labels are generated through a third-party API.

#### Problem

The provider experiences intermittent outages during peak shopping periods.

#### Guiding Questions

1. Should checkout fail?
2. How do you handle temporary outages?
3. How do you recover later?

#### Hints

[Click here](#Hints-of-Scenario-8)

### Scenario #9 (Do Nothing Scenario #2)

**Difficulty**: Hard
**Interview** Round: Behavioral/System Design
**Domain**: Database Optimization

#### Context

An engineer proposes adding five new indexes to improve search performance.

#### Problem

Current query latency is 35 ms, well below the 100 ms SLA. However, write performance may degrade.

#### Guiding Questions

1. Should you add the indexes?
2. What evidence would you gather first?
3. When is optimization premature?

#### Hints

[Click here](#Hints-of-Scenario-9)

### Scenario #10

**Difficulty**: Hard
**Interview Round**: System Design
**Domain**: Security

#### Context

Customers upload profile images and product reviews containing images.

#### Problem

Attackers begin uploading malicious files disguised as images.

#### Guiding Questions

1. How do you validate uploads?
2. Where should uploaded files be stored?
3. What security layers are needed?

#### Hints

[Click here](#Hints-of-Scenario-10)

### Scenario #11

**Difficulty**: Medium
**Interview Round**: System Design
**Domain**: Database (Replication Lag)

#### Context

Your SaaS application stores data in a primary database with multiple read replicas. After users update their profile, they are sometimes redirected to a page that still shows the old information.

#### Problem

Replication lag can reach 2–5 seconds during peak hours. Product reports this as a "bug."

#### Guiding Questions

1. Why is this happening?
2. How would you ensure users see their own recent changes?
3. Would you eliminate replicas entirely?

#### Hints

[Click here](#Hints-of-Scenario-11)

### Scenario #12

**Difficulty**: Medium
**Interview Round**: Backend Design
**Domain**: Background Jobs

#### Context

Your SaaS sends welcome emails, invoices, and password reset emails synchronously.

#### Problem

Email provider latency occasionally reaches 8 seconds, slowing API responses.

#### Guiding Questions

1. Should email sending happen inside the request?
2. How would you redesign the workflow?
3. What happens if the email service is unavailable?

#### Hints

[Click here](#Hints-of-Scenario-12)

### Scenario #13 (It Depends Scenario #2)

**Difficulty**: Hard
**Interview Round**: Behavioral + System Design
**Domain**: Microservices

#### Context

Your CTO wants to split the monolithic application into 20 microservices.

#### Problem

The current monolith serves 5,000 users with excellent uptime and a small engineering team of six developers.

#### Guiding Questions

1. Should you migrate now?
2. What problems are microservices solving?
3. What new operational costs will they introduce?

#### Hints

[Click here](#Hints-of-Scenario-13)

### Scenario #14

**Difficulty**: Easy
**Interview Round**: Coding
**Domain**: Security (JWT)

#### Context

Your frontend stores JWT access tokens in localStorage.

#### Problem

A penetration test highlights potential XSS risks.

#### Guiding Questions

1. Why is localStorage risky?
2. What alternatives exist?
3. How would refresh tokens work?

#### Hints

[Click here](#Hints-of-Scenario-14)

### Scenario #15

**Difficulty**: Hard
**Interview Round**: System Design
**Domain**: Rate Limiting

#### Context

A public API receives 15 million requests per day.

#### Problem

Some customers accidentally create infinite retry loops, overwhelming the service.

#### Guiding Questions

1. How would you implement rate limiting?
2. Per-user or per-IP?
3. How should clients know they've been throttled?

#### Hints

[Click here](#Hints-of-Scenario-15)

### Scenario #16

**Difficulty**: Medium
**Interview Round**: Frontend
**Domain**: React State Management

#### Context

A CRM dashboard has grown to dozens of pages using React Context for nearly all application state.

#### Problem

Small updates cause unnecessary re-renders throughout the application.

#### Guiding Questions

1. Why is this happening?
2. Would Redux, Zustand, or React Query help?
3. What state belongs where?

#### Hints

[Click here](#Hints-of-Scenario-16)

### Scenario #17

**Difficulty**: Medium
**Interview Round**: Backend
**Domain**: Deadlocks

#### Context

Two background workers update invoices and customer balances simultaneously.

#### Problem

Production logs show increasing deadlock errors.

#### Guiding Questions

1. Why do deadlocks occur?
2. How can transactions be redesigned?
3. Should deadlocks simply be retried?

#### Hints

[Click here](#Hints-of-Scenario-17)

### Scenario #18 (Do Nothing Scenario #3)

**Difficulty**: Medium
**Interview Round**: Behavioral
**Domain**: Frontend Performance

#### Context

Lighthouse score decreased from 98 to 95 after a UI redesign.

#### Problem

No users have complained, Core Web Vitals remain healthy, and business metrics are unchanged.

#### Guiding Questions

1. Should engineering stop feature development to regain 98?
2. What additional information would you collect?
3. When is optimization worthwhile?

#### Hints

[Click here](#Hints-of-Scenario-18)

### Scenario #19

**Difficulty**: Hard
**Interview Round**: System Design
**Domain**: API Versioning

#### Context

Thousands of customers integrate with your REST API.

#### Problem

A new feature requires changing the response format in a way that breaks existing clients.

#### Guiding Questions

1. How would you introduce the change?
2. URI versioning or header versioning?
3. How long should old versions remain supported?

#### Hints

[Click here](#Hints-of-Scenario-19)

### Scenario #20

**Difficulty**: Hard
**Interview Round**: System Design
**Domain**: Event-Driven Architecture

#### Context

Creating a new customer currently performs all actions synchronously:

- Create account
- Send email
- Create billing record
- Notify analytics
- Provision workspace

#### Problem

The API now takes 12 seconds to respond, and failures leave the system in inconsistent states.

#### Guiding Questions

Which tasks should become asynchronous?
How would services communicate?
How do you handle partial failures?

#### Hints

[Click here](#Hints-of-Scenario-20)

---

## Hints For Scenarios

### Hints Of Scenario #1

Strong Answer Should Include

- Expand → migrate → contract deployment
- Nullable column first
- Batched backfill
- Feature flags
- Dual-read/dual-write during migration
- Online schema migration tools
- Metrics on migration speed
- Rollback plan
- Validation queries
- Handling NULL values temporarily

### Hints Of Scenario #2

Strong Answer Should Include

- Redis cache
- Cache-aside pattern
- TTL selection based on update frequency
- Cache invalidation after product updates
- Cache warming
- Cache hit ratio monitoring

### Hints Of Scenario #3

Strong Answer Should Include

- Inventory reservation
- Atomic updates
- Distributed locking discussion
- Event-driven inventory updates
- Handling reservation expiration
- Business trade-offs
- Customer experience considerations
- Compensation workflows

### Hints Of Scenario #4

Strong Answer Should Include

- Idempotency keys
- Unique payment request IDs
- Database uniqueness constraints
- Retry-safe API
- Audit logs
- Duplicate detection
- Payment status endpoint

### Hints Of Scenario #5

Strong Answer Should Include

- Virtualized lists
- React.memo
- useMemo
- useCallback where appropriate
- Pagination vs infinite scroll
- Avoid unnecessary global state
- Lighthouse/Web Vitals
- React Profiler

### Hints Of Scenario #6

Strong Answer Should Include

- There is no universally correct answer.

Discussion should include:

- Stale prices
- Customer trust
- Cache invalidation complexity
- Separate caching of product metadata vs pricing
- Dynamic fragments
- CDN strategies
- Business priorities

A strong candidate recognizes that "it depends" on acceptable staleness.

### Hints Of Scenario #7

Strong Answer Should Include

- Canary deployment
- Feature flags
- Automated rollback
- Error monitoring
- Checkout conversion metrics
- Logs
- Tracing
- Incident communication
- Postmortem process

### Hints Of Scenario #8

Strong Answer Should Include

- Queue requests
- Retry with exponential backoff
- Circuit breaker
- Dead-letter queue
- Manual recovery tools
- Customer communication
- Monitoring API availability

### Hints Of Scenario #9

Strong Answer Should Include

- The strongest answer may be not to change anything yet.

Discussion should include:

- Measure before optimizing
- Query plans
- Production metrics
- Write amplification
- Index maintenance costs
- Future scalability considerations
- Avoiding unnecessary complexity

### Hints Of Scenario #10

Strong Answer Should Include

- MIME type validation
- File signature (magic number) verification
- Size limits
- Virus scanning
- Object storage (e.g., S3)
- Randomized filenames
- Signed URLs
- Content Security Policy (CSP)
- Rate limiting
- Logging and alerting
- Restrict executable content

### Hints Of Scenario #11

Strong Answer Should Include

- Understanding eventual consistency
- Read-after-write consistency
- Routing recent reads to the primary
- Sticky sessions or session-based routing
- Monitoring replication lag
- Trade-offs between latency and consistency
- Why removing replicas may hurt scalability

### Hints Of Scenario #12

Strong Answer Should Include

- Job queues (BullMQ, RabbitMQ, SQS)
- Fire-and-forget architecture
- Retry policies
- Dead-letter queues
- Idempotent workers
- Monitoring queue depth
- Separating critical from non-critical tasks

### Hints Of Scenario #13

Strong Answer Should Include

- There may be no reason to migrate today.

Discussion should include:

- Conway's Law
- Team size considerations
- Operational complexity
- Distributed debugging
- Deployment independence
- Network failures
- Database ownership
- "Microservices are not a goal"

A strong candidate challenges assumptions rather than blindly agreeing.

### Hints Of Scenario #14

Strong Answer Should Include

- HttpOnly cookies
- Secure + SameSite flags
- Short-lived access tokens
- Refresh token rotation
- XSS considerations
- CSRF protection
- Logout invalidation strategy

### Hints Of Scenario #15

Strong Answer Should Include

- Token bucket or leaky bucket algorithms
- Redis-based counters
- HTTP 429 responses
- Retry-After headers
- Different limits for authenticated users
- Burst handling
- Monitoring abuse patterns

### Hints Of Scenario #16

- Strong Answer Should Include
- Local vs global state
- Server state vs client state
- React Query/TanStack Query
- Context limitations
- Component isolation
- Memoization
- State normalization

### Hints Of Scenario #17

Strong Answer Should Include

- Consistent locking order
- Smaller transactions
- Retry logic
- Isolation levels
- Database diagnostics
- Transaction boundaries
- Avoiding long-running transactions

### Hints Of Scenario #18

Strong Answer Should Include

- The best decision may be not to prioritize this.

Discussion should include:

- User impact vs benchmark scores
- Business priorities
- Opportunity cost
- Monitoring real-user metrics (RUM)
- Avoiding vanity metrics

### Hints Of Scenario #19

Strong Answer Should Include

- Backward compatibility
- Versioning strategies
- Deprecation policy
- API documentation
- Sunset timelines
- Monitoring client adoption
- Communication with customers

### Hints Of Scenario #20

Strong Answer Should Include

- Event-driven architecture
- Message broker (Kafka, RabbitMQ, SQS)
- Domain events
- Eventual consistency
- Idempotent consumers
- Saga pattern (if appropriate)
- Retry mechanisms
- Dead-letter queues
- Distributed tracing
- Monitoring event failures
