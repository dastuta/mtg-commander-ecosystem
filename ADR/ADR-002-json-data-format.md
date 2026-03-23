# ADR-002: JSON as the Standard Data Format

## Status

Accepted

## Context

For ecosystem components to communicate, they need a shared data format. We evaluated several options:

- **JSON**: Human-readable, widely supported
- **XML**: Verbose, complex parsing
- **CSV**: Simple but limited structure
- **Protocol Buffers**: Efficient but requires code generation
- **YAML**: Similar to JSON but less standardized

## Decision

**JSON** will be the standard data format for the MTG Commander Ecosystem.

## Rationale

### JSON Advantages

1. **Universal Support**
   - Every major programming language has native JSON support
   - No code generation or compilation needed
   - Easy debugging with human-readable structure

2. **Ecosystem Integration**
   - Works with every web technology
   - Native browser support (JavaScript)
   - Easy to store in databases (PostgreSQL, MongoDB, etc.)

3. **Tooling**
   - VS Code has excellent JSON support
   - JSON Schema for validation
   - Easy to convert to other formats when needed

4. **Community Standards**
   - MTGJSON, Scryfall API, and most MTG tools use JSON
   - Lower barrier to entry for contributors

### Trade-offs Accepted

- Larger file sizes than binary formats (acceptable for game data)
- No native support for dates (we use ISO 8601 strings)
- Limited type system (we use JSON Schema for validation)

## Schema Requirements

All JSON files MUST:

1. Include a `version` field (e.g., `"version": "1.0.0"`)
2. Include a `type` field indicating the content type
3. Use ISO 8601 timestamps
4. Validate against JSON Schema

## Example

```json
{
  "version": "1.0.0",
  "type": "game",
  "id": "550e8400-e29b-41d4-a716-446655440000",
  "createdAt": "2024-01-15T19:30:00Z",
  // ... game data
}
```

## Alternatives Considered

### Protocol Buffers
- Pros: Smaller files, faster parsing, type safety
- Cons: Requires compilation, harder to debug, less human-readable

### MessagePack
- Pros: Binary efficiency, good library support
- Cons: Not human-readable, less tooling support

### XML
- Pros: Schema validation, namespaces
- Cons: Verbose, complex parsing, dated

## Consequences

### Positive
- Easy integration with any tool or language
- Human-readable for debugging
- Native browser support
- Wide tooling ecosystem

### Negative
- Larger file sizes than binary alternatives
- Slightly slower parsing than binary
- No built-in date type

## References

- [json-schema.org](https://json-schema.org/)
- [MDN: JSON](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON)
- [Scryfall API](https://scryfall.com/docs/api) (uses JSON)
- [MTGJSON](https://mtgjson.com/) (uses JSON)
