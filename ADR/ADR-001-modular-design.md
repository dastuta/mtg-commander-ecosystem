# ADR-001: Modular Ecosystem Design

## Status

Accepted

## Context

Traditional applications tend to grow into monolithic systems where all features are tightly coupled. This creates several problems:

- **Single point of failure**: One broken feature affects everything
- **Vendor lock-in**: Users must use the entire system or nothing
- **Development bottleneck**: All features must be built by one team
- **Learning curve**: New users face full complexity immediately

For MTG Commander tracking, different user groups have vastly different needs:
- Casual players want simple life tracking
- Stats-focused players want detailed analytics
- Tournament organizers need different features entirely

## Decision

We will build a **modular ecosystem** where:
1. Each component is a standalone tool
2. Components communicate through a standardized data format (JSON)
3. Users can mix and match tools based on their needs
4. The system remains functional even if individual components are unavailable

## Architecture

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Tracker   │────▶│    JSON     │◀────│  Statistics │
│    (App)    │     │   Export    │     │   Engine    │
└─────────────┘     └─────────────┘     └─────────────┘
       │                  ▲                    │
       │                  │                    │
       ▼                  │                    ▼
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│    REST     │────▶│   Server    │◀────│    Deck     │
│    Client   │     │   (VPS)     │     │  Analyzer   │
└─────────────┘     └─────────────┘     └─────────────┘
```

## Consequences

### Positive
- Users can start simple and add complexity as needed
- Different teams can maintain different components
- Tools can be replaced without breaking the ecosystem
- Easier to test and maintain individual components

### Negative
- More complexity in documentation and discovery
- Users must choose their own tool combinations
- Data sync between tools requires careful handling
- More projects to maintain overall

## Alternatives Considered

### 1. Monolithic Application
One app with all features. Rejected because it creates vendor lock-in and development bottlenecks.

### 2. Plugin System
Single app with plugin architecture. More complex to develop and limits contribution to plugin-compatible code.

### 3. No Standardization
Let tools define their own formats. Rejected because it prevents interoperability.

## Implementation Notes

- Each tool MUST document how it imports/exports the standard format
- The JSON schema is the "contract" between components
- Breaking changes to the schema require major version bump

## References

- [Unix Philosophy](https://en.wikipedia.org/wiki/Unix_philosophy)
- [Microservices patterns](https://microservices.io/patterns/index.html)
- [JSON Schema](https://json-schema.org/)
