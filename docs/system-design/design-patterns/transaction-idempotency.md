# Transaction Idempotency

An idempotent operation can be safely repeated without changing the final result beyond the first successful execution.

## Why It Matters

Distributed systems retry requests because networks fail, timeouts happen, and clients may not know whether a previous request succeeded. Without idempotency, retries can create duplicate payments, duplicate orders, or repeated side effects.

## Core Concepts

### Idempotency Key

The client sends a unique key for an operation.

```http
POST /payments
Idempotency-Key: 7d5f3b7a-payment-1001
```

The server stores the key and result. If the same key is received again, the server returns the original result instead of performing the operation again.

### Transaction Boundary

The idempotency record and business change should be committed together when possible.

Example:

1. Receive payment request with idempotency key.
2. Check whether key already exists.
3. If it exists, return stored result.
4. If it does not exist, create payment and store key/result in one transaction.

## Isolation Levels: Read Committed and Serializable

Transaction isolation affects how concurrent requests interact.

| Isolation level | Guarantee | Tradeoff |
| --- | --- | --- |
| Read Committed | Reads only committed data | Allows non-repeatable reads and phantoms |
| Serializable | Behaves like transactions ran one at a time | May abort transactions and require retries |

For high-value operations, the application must be designed for safe retries even when the database aborts a transaction.

## Related Pattern: PRG

The POST/Redirect/GET pattern avoids accidental form resubmission in browser flows:

1. Browser submits a POST.
2. Server processes the request.
3. Server redirects to a GET page.
4. Refreshing the page repeats the GET, not the POST.

PRG helps user experience, but it is not a full replacement for server-side idempotency.

## Common Mistakes

- Generating idempotency keys on the server after the duplicate request has already arrived.
- Storing the key separately from the business transaction.
- Expiring keys too quickly for real retry behavior.
- Assuming HTTP `PUT` is automatically safe without correct server logic.

## Related Topics

- [CQRS](cqrs.md)
- [REST](../rest.md)

## References

- Stripe idempotent requests: <https://docs.stripe.com/api/idempotent_requests>
- PostgreSQL transaction isolation: <https://www.postgresql.org/docs/current/transaction-iso.html>
