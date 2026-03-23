# Contributing to MTG Commander Ecosystem

Thank you for your interest in contributing to the MTG Commander Ecosystem!

## Ways to Contribute

### 1. Propose a New Component

Found a tool that should be part of the ecosystem? Open an issue with:

- **Tool name** and description
- **What it does** (tracker, statistics, analyzer, etc.)
- **How it integrates** with the standard data format
- **Link to repository** (if open source)

### 2. Add Integration Support

Does your existing tool use the standard format? Add it to [INTEGRATIONS.md](./INTEGRATIONS.md):

- **Tool name** and description
- **Supported features** (import/export/both)
- **Link to repository**
- **Screenshots** (optional)

### 3. Improve the Specification

Found an issue with the data schema? Propose changes:

1. Open an issue describing the problem or improvement
2. Submit a PR with changes to [DATA_SCHEMA.md](./DATA_SCHEMA.md)
3. Include rationale and examples
4. Ensure backward compatibility considerations

### 4. Build New Tools

Want to create a new tool for the ecosystem?

1. Follow the [Architecture Overview](../README.md)
2. Implement the [Data Schema](./DATA_SCHEMA.md)
3. Document how to integrate
4. Add to [INTEGRATIONS.md](./INTEGRATIONS.md)

## Standards

### Code Standards

- Use meaningful variable names
- Include comments for complex logic
- Follow language-specific conventions
- Write tests for core functionality

### Documentation Standards

- Clear description of purpose
- Installation instructions
- Usage examples
- API documentation (if applicable)

### Data Format

- Always include `version` field
- Use ISO 8601 for timestamps
- Validate against JSON schema
- Preserve unknown custom fields

## Communication

- **Issues**: Use GitHub Issues for bug reports and feature requests
- **Discussions**: Use GitHub Discussions for questions and ideas
- **PRs**: Keep them focused and well-described

## Code of Conduct

This project follows the [Contributor Covenant](https://www.contributor-covenant.org/).

## License

By contributing, you agree that your contributions will be released under the same license as the project (specified in each repository).

## Questions?

Open an issue or start a discussion if you have questions!
