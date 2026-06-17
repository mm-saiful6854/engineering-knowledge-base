# Multi-Tenant Architecture

Multi-tenant architecture lets one software system serve multiple customers, called tenants, while keeping each tenant's data and configuration logically isolated.

## Why It Matters

Most SaaS products need tenant isolation, shared infrastructure, billing boundaries, authorization rules, and operational visibility per customer.

## Core Concepts

### SaaS

Software as a Service delivers software over the internet, commonly with subscription billing.

Benefits:

- Lower setup cost for customers
- Centralized upgrades
- Easier access from multiple locations
- Elastic scaling when designed well

### Tenant Isolation Models

| Model | Description | Tradeoff |
| --- | --- | --- |
| Shared database, shared schema | All tenants share tables with a `tenant_id` column | Cost efficient, but isolation depends on careful queries and authorization |
| Shared database, separate schema | Tenants share infrastructure but have separate schemas | Better isolation, more operational complexity |
| Separate database per tenant | Each tenant has its own database | Strong isolation, higher cost and management overhead |

### Performance Metrics

Track these metrics per service and, when possible, per tenant:

- Latency: how long one request takes.
- Throughput: how much work the system handles over time.
- Availability: percentage of time the service is usable.
- Error rate: percentage of failed requests.

## Common Mistakes

- Forgetting tenant filters in database queries.
- Designing authorization without tenant boundaries.
- Letting one noisy tenant degrade every other tenant.
- Making tenant migrations and backups an afterthought.
- Treating horizontal scaling as a replacement for tenant isolation.

## Related Topics

- [System Design Foundations](foundations.md)
- [Stateful and Stateless Architecture](stateful-stateless.md)

## References

- IBM multi-tenant overview: <https://www.ibm.com/think/topics/multi-tenant>
- Frontegg SaaS architecture guide: <https://frontegg.com/guides/saas-applications-architecture-the-how>
