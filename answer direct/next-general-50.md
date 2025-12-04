Perfect! Here’s the continuation: the **remaining 50–70+ questions** in the same PDF-style format, completing your full **120 Q&A prep kit**.

---

# **11. Kafka / Messaging & Event-Driven Architecture (continued)**

**Q51:** Explain Kafka topic partitioning.
**A51:**

* Topics divided into partitions to allow parallel consumption
* Each partition is ordered; messages processed sequentially
* Consumer groups can read from partitions independently

**Q52:** How do you handle message duplication in Kafka?
**A52:**

* Use **idempotent operations** on consumer side
* Configure **acks=all** for producer reliability
* Enable **exactly-once semantics** if needed

**Q53:** How did you monitor Kafka in ULM?
**A53:**

* Lag monitoring via Kafka consumer metrics
* Alerts for failed consumers
* Logs collected in ELK stack

**Q54:** Difference between Kafka and ActiveMQ/RabbitMQ?
**A54:**

* Kafka: Distributed, high throughput, persistent log
* RabbitMQ: Broker-based, lower throughput, message queue

**Q55:** How do you implement event-driven flow for subscription creation?
**A55:**

* API call creates subscription
* Event published to Kafka topic
* Consumer microservice updates ULM DB
* Event replay ensures consistency in case of failure

---

# **12. Database / SQL / PL-SQL (continued)**

**Q56:** How do you optimize migration scripts?
**A56:**

* Chunk processing for large datasets
* Use bulk insert/update statements
* Minimize indexes during migration
* Rebuild indexes after migration

**Q57:** How do you validate migrated data?
**A57:**

* Row count comparison between staging and production
* Key field reconciliation (userId, subscriptionId)
* Sample data validation manually or via automated scripts

**Q58:** How do you manage transactions in PL-SQL?
**A58:**

* Use `COMMIT` and `ROLLBACK`
* Exception handling with `WHEN OTHERS`
* Savepoints for partial rollback

**Q59:** How do you handle database deadlocks?
**A59:**

* Use proper indexing and optimized queries
* Lock in consistent order
* Retry logic with backoff

**Q60:** What is the purpose of staging tables in migration?
**A60:**

* Temporary storage for bulk CSV data
* Pre-processing and validation before moving to main table
* Improves performance and reduces impact on production

**Q61:** How do you handle millions of records without timeouts?
**A61:**

* Pagination or chunk-based processing
* Index optimization
* Batch commits

---

# **13. DevOps / CI-CD / Docker / Cloud (continued)**

**Q62:** How do you configure Jenkins pipelines for multiple microservices?
**A62:**

* Multi-branch pipeline per microservice
* Build, test, Docker image creation, push, deployment stages
* Environment-specific parameters for DEV, QA, PROD

**Q63:** How do you handle rollbacks?
**A63:**

* Rollback Docker image to previous tag
* Revert DB migrations via Liquibase/Flyway
* Restore backups if needed

**Q64:** Why do you use Liquibase/Flyway?
**A64:**

* Version control for database schema
* Automated migration scripts in CI/CD
* Supports rollback and tracking

**Q65:** How do you use Docker for ULM services?
**A65:**

* Containerize services with dependencies
* Ensure consistent runtime across environments
* Use Docker-compose for local testing of multiple microservices

**Q66:** How do you secure microservices in cloud?
**A66:**

* Network security groups / VPC
* HTTPS / TLS
* OAuth2 / JWT tokens

**Q67:** How do you manage environment variables in Docker?
**A67:**

* `.env` files for secrets and config
* Kubernetes secrets/configmaps in production

---

# **14. Performance / Optimization (continued)**

**Q68:** How did you improve API throughput?
**A68:**

* Optimized DB queries
* Asynchronous processing with Kafka
* Caching of frequently used data

**Q69:** How did you handle concurrent user registrations?
**A69:**

* Use DB transactions to avoid race conditions
* Kafka queue to process asynchronously
* Retry on failure

**Q70:** How do you minimize downtime during migration?
**A70:**

* Migrate in chunks
* Lower environment validation first
* Parallel execution with monitoring

**Q71:** How do you debug performance issues in production?
**A71:**

* Analyze logs and metrics
* Profile with Java tools (JVisualVM, YourKit)
* Identify slow SQL queries or high latency microservices

---

# **15. Microservices / System Design**

**Q72:** How do you design subscription service?
**A72:**

* REST endpoints for CRUD operations
* Kafka events for async updates
* DB table: MT_SUB + EXT_SUB_ATR
* Service layer for business logic

**Q73:** How do you handle user/account/group relationships?
**A73:**

* User -> Account -> Subscription -> Group
* Maintain foreign key relationships
* Sync via reconciliation API if discrepancies

**Q74:** Why use asynchronous event-driven flow?
**A74:**

* Decouples services
* Scales better for millions of users
* Failure handling via retries and DLQ

**Q75:** How do you migrate legacy users to new stack?
**A75:**

* Extract CSV from legacy DB
* Load into staging table
* Validate and migrate in chunks to main table
* Reconcile with ULM data

**Q76:** How do you design enriched user flow?
**A76:**

* Temporary user with contact number
* Limited access to offers/campaign
* Upgrade to full user upon registration
* Delete enriched user after upgrade

---

# **16. Behavioral / STAR-format (continued)**

**Q77:** Describe a situation where you fixed a critical bug.
**A77 (STAR):**

* **S:** Users unable to register due to DB lock
* **T:** Fix issue without downtime
* **A:** Identified blocking transaction, optimized SQL, reprocessed failed users
* **R:** Registration restored; no data loss

**Q78:** How did you improve team efficiency?
**A78 (STAR):**

* **S:** Multi-country team had delayed migrations
* **T:** Reduce coordination lag
* **A:** Implemented standardized scripts, checklists, and weekly sync
* **R:** Faster migration cycles, reduced errors

**Q79:** How did you handle unexpected migration failure?
**A79 (STAR):**

* **S:** Chunk migration failed at 60%
* **T:** Ensure data consistency
* **A:** Rolled back failed chunk, reprocessed after fixing script, added logging
* **R:** Migration completed successfully with validation

**Q80:** Give an example of improving API reliability.
**A80 (STAR):**

* **S:** REST APIs occasionally failed under load
* **T:** Ensure high availability
* **A:** Added circuit breaker, retries, and monitoring
* **R:** 99.9% API uptime achieved

---

# **17. Trending / General Technical Questions**

**Q81:** Explain JWT token structure.
**A81:** Header.Payload.Signature; Base64-encoded; used for stateless authentication

**Q82:** Difference between SAML and OIDC?
**A82:**

* SAML: XML-based, mainly for enterprise SSO
* OIDC: JSON-based, OAuth2 protocol for modern applications

**Q83:** How does multi-factor authentication work?
**A83:**

* 1FA: username/password
* 2FA: username/password + OTP
* 3FA: username/password + OTP + device verification

**Q84:** How do you handle multiple versions of microservices?
**A84:**

* Use versioned APIs
* Deploy side-by-side
* Service discovery handles routing

**Q85:** What is eventual consistency in ULM context?
**A85:**

* Kafka events may take time to propagate
* Reconciliation API ensures data consistency across ULM and VF

**Q86:** How do you optimize Kafka producer?
**A86:**

* Batch records
* Compression (gzip/snappy)
* Async send with retries

**Q87:** How do you monitor API SLA?
**A87:**

* Track latency, error rate, throughput
* Alerts for SLA violations

**Q88:** How do you secure sensitive user data?
**A88:**

* Encryption at rest and in transit
* Masking PII in logs
* Role-based access

**Q89:** How do you handle schema changes in DB?
**A89:**

* Version control via Liquibase/Flyway
* Backward-compatible changes first
* Test migrations in staging

**Q90:** How do you test microservices integration?
**A90:**

* Contract testing
* Integration tests in staging environment
* Mock external dependencies where needed

---

# **18. Miscellaneous / Advanced**

**Q91:** Difference between synchronous and asynchronous APIs?
**A91:** Sync: immediate response required
Async: processing in background (Kafka events)

**Q92:** How do you handle API rate limits?
**A92:** Throttling, queuing, or returning HTTP 429

**Q93:** How do you debug distributed systems?
**A93:** Correlate logs via trace IDs, use monitoring tools, reproduce in lower env

**Q94:** How do you handle legacy system integration?
**A94:** Adapter pattern, API gateway, async message queue

**Q95:** How do you perform database indexing?
**A95:** Index frequently queried columns, use composite indexes where needed, monitor query plans

**Q96:** What are common Kafka consumer pitfalls?
**A96:**

* Not committing offsets
* Slow consumers blocking partitions
* Not handling duplicate messages

**Q97:** How do you ensure CI/CD reliability?
**A97:** Automated tests, rollback scripts, staging verification

**Q98:** How do you handle configuration management?
**A98:** Profiles in Spring Boot, environment variables, secrets management

**Q99:** How do you manage dependencies in Maven?
**A99:** Use `dependencyManagement`, avoid version conflicts, clean builds

**Q100:** What is your approach to handling critical production bugs?
**A100:** Immediate analysis, isolate impact, fix, deploy, communicate with stakeholders

**Q101:** How do you handle millions of users in ULM?
**A101:** Efficient DB queries, Kafka async processing, microservices scaling, caching

**Q102:** How do you ensure data security in cloud?
**A102:** IAM policies, VPC isolation, encryption, auditing

**Q103:** How do you monitor Kafka lag in production?
**A103:** Kafka consumer metrics, alerts if lag > threshold

**Q104:** How do you design REST API for large payloads?
**A104:** Pagination, filtering, compression

**Q105:** How do you migrate ULM legacy data quarterly?
**A105:** Extract CSV → staging → main table → reconciliation → re-index → monitor

**Q106:** How do you optimize SQL scripts for large datasets?
**A106:** Chunk processing, bulk operations, indexed joins, avoid nested queries

**Q107:** How do you handle inter-service failures?
**A107:** Retry, circuit breaker, fallback, alerting

**Q108:** How do you ensure logging and monitoring across services?
**A108:** Centralized ELK stack, consistent log format, trace IDs

**Q109:** How do you implement session timeout?
**A109:** Spring Security session management; 30 min web, 120 min retail/admin

**Q110:** How do you implement enriched user logic?
**A110:** Temporary user with minimal details, upgrade on full registration, delete temp user

**Q111:** How do you maintain backward compatibility in APIs?
**A111:** Versioning, optional fields, maintain old endpoints until clients upgrade

**Q112:** How do you scale Kafka consumers?
**A112:** Increase partitions, add consumer instances in the same consumer group

**Q113:** How do you debug slow SQL queries?
**A113:** Use `EXPLAIN PLAN`, check indexes, optimize joins, minimize full table scans

**Q114:** How do you implement unit and integration testing?
**A114:** JUnit + Mockito for unit tests, Postman/ReadyAPI for integration

**Q115:** How do you handle high-volume REST traffic?
**A115:** Caching, load balancers, async processing, horizontal scaling

**Q116:** How do you manage schema changes during migration?
**A116:** Staging table validation, backward-compatible changes, script versioning

**Q117:** How do you prevent downtime during deployment?
**A117:** Blue-green deployments, rolling updates, monitoring

**Q118:** How do you handle partial migration failure?
**A118:** Rollback failed chunk, log errors, retry after fix

**Q119:** How do you ensure data consistency across ULM & VF systems?
**A119:** Kafka events, reconciliation API, idempotent operations

**Q120:** How do you handle multi-country regulatory compliance (e.g., GDPR)?
**A120:** Data encryption, masking PII, data retention policies, consent management

---

✅ **All 120 questions are now ready in PDF-style format**, combining:

* Technical + trending questions
* Project-specific + behavioral STAR answers
* DevOps, Kafka, SQL, Microservices, REST, Migration, Performance

---

I can **now create a single ready-to-download PDF file** containing:

* All 120 Q&A
* STAR stories
* Cheat sheets for tech & behavioral questions
* Mock interview script

Do you want me to generate the **final complete PDF file** next?
