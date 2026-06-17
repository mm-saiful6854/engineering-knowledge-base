# HTTP, RPC, gRPC, and JSON-RPC

Modern services need both a transport protocol and an interaction style. HTTP defines how messages move across the web. REST and RPC styles define how clients think about operations.

## Why It Matters

Choosing the wrong communication style can make a system harder to debug, slower than necessary, or difficult for other teams to consume.

## HTTP/1.1

HTTP/1.1 is text-oriented and widely supported.

Key points:

- Request and response messages are human-readable.
- Headers are repeated on each request.
- Browsers often open multiple TCP connections to fetch assets in parallel.
- A slow request can block later work on the same connection.

HTTP/1.1 remains a good default for public web APIs because every browser, proxy, and client library understands it.

## HTTP/2

HTTP/2 keeps HTTP semantics, such as methods and status codes, but changes how data is framed.

Key points:

- Uses binary frames.
- Supports multiplexing multiple streams over one TCP connection.
- Compresses headers with HPACK.
- Enables efficient streaming patterns.

HTTP/2 is the foundation for gRPC.

## RPC

Remote Procedure Call is an interaction style where the client calls a remote operation as if it were a local function.

Example mental model:

```text
getUser(userId) -> network -> user service -> response
```

RPC is action-oriented. REST is resource-oriented.

## JSON-RPC

JSON-RPC is a lightweight RPC protocol that sends method names and parameters as JSON.

Example:

```json
{
  "jsonrpc": "2.0",
  "method": "getUser",
  "params": { "id": 42 },
  "id": 1
}
```

Use it when:

- The API is internal.
- Operations are naturally command-like.
- You want simple request/response messages without schema tooling.

## gRPC

gRPC is a high-performance RPC framework built on HTTP/2 and Protocol Buffers.

Use it when:

- Services communicate internally at high volume.
- Strong contracts between teams matter.
- Streaming is important.
- Payload size and performance matter.

Example service contract:

```protobuf
service UserService {
  rpc GetUser (GetUserRequest) returns (User);
}
```

## Comparison

| Style | Best for | Strength | Tradeoff |
| --- | --- | --- | --- |
| REST over HTTP | Public APIs | Familiar and browser-friendly | Can become inconsistent without discipline |
| JSON-RPC | Simple internal commands | Easy to implement and debug | Weak typing by default |
| gRPC | Internal service communication | Fast, typed, streaming-friendly | Browser support needs gRPC-Web or a proxy |

## Common Mistakes

- Using gRPC for a public API when simple HTTP/JSON would be easier for consumers.
- Calling an API RESTful only because it uses HTTP.
- Ignoring network failure because the client code looks like a local function call.
- Over-optimizing protocol performance before understanding the bottleneck.

## Related Topics

- [REST](rest.md)
- [SOAP](soap.md)
- [Server-Sent Events](server-sent-events.md)

## References

- HTTP/2 specification: <https://www.rfc-editor.org/rfc/rfc9113>
- gRPC documentation: <https://grpc.io/docs/>
- JSON-RPC specification: <https://www.jsonrpc.org/specification>
