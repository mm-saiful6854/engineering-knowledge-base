# Engineering Knowledge Base

A Markdown-first engineering knowledge base for practicing, revising, and sharing software engineering concepts with the community.

The repository is organized as clean technical notes rather than raw exports from Notion or any other note-taking tool. Each page should be readable directly on GitHub and also build into a docs website with MkDocs Material.

## Read Online

GitHub Pages site:

<https://mm-saiful6854.github.io/engineering-knowledge-base/>

## Topics

| Area | Status | Start here |
| --- | --- | --- |
| System Design | Active | [System Design](docs/system-design/index.md) |
| Database | Planned | [Database](docs/database/index.md) |
| Backend | Planned | [Backend](docs/backend/index.md) |
| Programming Fundamentals | Planned | [Programming Fundamentals](docs/programming-fundamentals/index.md) |
| DevOps | Planned | [DevOps](docs/devops/index.md) |

## System Design Notes

- [System Design Foundations](docs/system-design/foundations.md)
- [HTTP, RPC, gRPC, and JSON-RPC](docs/system-design/http-rpc-grpc-json-rpc.md)
- [REST](docs/system-design/rest.md)
- [SOAP](docs/system-design/soap.md)
- [Server-Sent Events](docs/system-design/server-sent-events.md)
- [Single Sign-On and OAuth](docs/system-design/sso-oauth.md)
- [Stateful and Stateless Architecture](docs/system-design/stateful-stateless.md)
- [Multi-Tenant Architecture](docs/system-design/multi-tenant-architecture.md)
- [Domain-Driven Design](docs/system-design/domain-driven-design.md)
- [UML](docs/system-design/uml.md)
- [Object-Oriented Programming](docs/system-design/oop.md)
- [Design Patterns](docs/system-design/design-patterns/index.md)

## Local Preview

```bash
python3 -m venv .venv
source .venv/bin/activate
python3 -m pip install -r requirements.txt
mkdocs serve
```

Build the site before publishing:

```bash
mkdocs build --strict
```

## Contributing

Corrections, clearer explanations, and new topic notes are welcome through issues and pull requests. See [CONTRIBUTING.md](CONTRIBUTING.md) before opening a PR.

## License

Code and automation in this repository are licensed under the [MIT License](LICENSE).

Written knowledge-base content is licensed under [Creative Commons Attribution 4.0 International](CONTENT_LICENSE.md).
