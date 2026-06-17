# SOAP

SOAP stands for Simple Object Access Protocol. It is a formal messaging protocol for exchanging structured XML messages between systems.

## Why It Matters

SOAP is less common for new public APIs than REST, but it still appears in enterprise systems, banking, payments, legacy integrations, and systems that need strict contracts and message-level standards.

## Core Concepts

SOAP messages are usually XML documents wrapped in a SOAP envelope.

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <GetCustomer>
      <CustomerId>42</CustomerId>
    </GetCustomer>
  </soap:Body>
</soap:Envelope>
```

Important related standards:

- WSDL describes available operations and message formats.
- WS-Security defines message-level security.
- WS-Addressing carries routing metadata.
- WS-ReliableMessaging supports reliable delivery patterns.

## SOAP and REST

| Area | SOAP | REST |
| --- | --- | --- |
| Style | Protocol | Architectural style |
| Payload | XML | Usually JSON, sometimes XML or other formats |
| Contract | Strong WSDL contract | Often OpenAPI or documentation |
| Best fit | Enterprise integrations with strict standards | Public and web-friendly APIs |
| Error model | SOAP fault | HTTP status codes plus response body |

## When To Use SOAP

- An existing partner requires SOAP.
- The organization depends on WS-* standards.
- Contract-first integration is more important than developer friendliness.
- The system is in a domain with mature SOAP tooling and governance.

## Common Mistakes

- Choosing SOAP for a new simple web API without a real contract or compliance need.
- Treating SOAP and REST as only XML versus JSON.
- Ignoring the operational cost of WSDL, code generation, and enterprise tooling.

## Related Topics

- [REST](rest.md)
- [HTTP, RPC, gRPC, and JSON-RPC](http-rpc-grpc-json-rpc.md)

## References

- AWS comparison of SOAP and REST: <https://aws.amazon.com/compare/the-difference-between-soap-rest/>
- W3C SOAP specification: <https://www.w3.org/TR/soap/>
