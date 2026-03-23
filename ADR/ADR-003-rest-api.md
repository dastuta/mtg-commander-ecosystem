# ADR-003: REST API as Primary Network Protocol

## Status

Accepted

## Context

When components need to communicate over a network (e.g., syncing to a self-hosted server), we need a protocol. Options evaluated:

- **REST**: HTTP-based, resource-oriented
- **GraphQL**: Query-based, flexible responses
- **WebSocket**: Real-time, bidirectional
- **gRPC**: High-performance, binary protocol

## Decision

**REST** will be the primary protocol for the MTG Commander Ecosystem server.

## Rationale

### REST Advantages

1. **Simplicity**
   - Easy to understand and implement
   - Uses standard HTTP methods (GET, POST, PUT, DELETE)
   - No complex query language to learn

2. **Universal Support**
   - Every programming language has HTTP libraries
   - Works with browsers, mobile apps, scripts
   - Easy to test with curl or Postman

3. **Tooling**
   - Reverse proxy support (nginx, Caddy)
   - Authentication middleware (JWT, OAuth)
   - Caching and rate limiting
   - API documentation (OpenAPI/Swagger)

4. **MTG Ecosystem Alignment**
   - Similar to Scryfall's API approach
   - Familiar pattern for web developers

### When to Use Alternatives

- **GraphQL**: Client needs flexible data shaping (complex dashboards)
- **WebSocket**: Real-time updates during active games
- **File Transfer**: Manual export/import workflows

## API Design Principles

### Resources

```
/api/v1/games          - List/create games
/api/v1/games/:id      - Get/update/delete game
/api/v1/players        - List/create players
/api/v1/players/:id    - Get/update/delete player
/api/v1/groups         - List/create groups
/api/v1/stats/player/:id - Player statistics
```

### Methods

| Method | Action |
|--------|--------|
| GET | Retrieve resource(s) |
| POST | Create new resource |
| PUT | Replace resource |
| PATCH | Partial update |
| DELETE | Remove resource |

### Response Format

All responses return JSON:

```json
{
  "success": true,
  "data": { /* resource or array */ },
  "meta": {
    "total": 100,
    "page": 1,
    "perPage": 20
  }
}
```

### Error Format

```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid game data",
    "details": [
      { "field": "players", "message": "Minimum 2 players required" }
    ]
  }
}
```

## Consequences

### Positive
- Simple to implement and understand
- Wide tooling and documentation
- Easy to proxy and cache
- Good for most use cases

### Negative
- Over-fetching for complex queries
- Multiple roundtrips for related data
- Less flexible than GraphQL

## Implementation Notes

### Authentication
- JWT tokens for stateless auth
- Token refresh flow
- Optional: OAuth2 for social login

### Rate Limiting
- Default: 100 requests/minute per user
- Authenticated: 1000 requests/minute
- Configurable per deployment

### Caching
- GET requests are cacheable
- Use ETags for conditional requests

## References

- [REST API Tutorial](https://restfulapi.net/)
- [OpenAPI Specification](https://swagger.io/specification/)
- [Scryfall API Design](https://scryfall.com/docs/api)
