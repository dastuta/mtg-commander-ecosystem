# MTG Commander Ecosystem

> **An open, modular ecosystem for Magic: The Gathering Commander tracking, statistics, and deck analysis.**

## Vision

Create a community-driven, open-source alternative to proprietary tools like playgroup.gg. Instead of building one monolithic application, we design a **modular ecosystem** where different tools can work together through a shared data format.

Every player group has different needs. Some want a simple life tracker during games, others want deep statistical analysis. This ecosystem allows you to:

- **Track games** with your preferred tool
- **Export data** in a standardized format
- **Analyze** with any compatible statistics engine
- **Extend** with custom tools that understand the shared schema

## Core Principles

1. **Modularity** - Each component does one thing well
2. **Interoperability** - Tools communicate through open standards (JSON)
3. **Decentralization** - No mandatory cloud service; self-hosting supported
4. **Community** - Open to contributions and extensions

## Ecosystem Components

```
┌─────────────────────────────────────────────────────────────────────┐
│                        CLIENT LAYER                                  │
├──────────────┬──────────────┬──────────────┬───────────────────────┤
│   TRACKER    │  STATISTICS  │  DECK        │   OTHER TOOLS         │
│   (PWA/App)  │    VIEWER    │  ANALYZER    │                       │
└──────┬───────┴──────┬───────┴──────┬───────┴───────────┬─────────┘
       │               │              │                    │
       ▼               ▼              ▼                    │
┌──────────────────────────────────────────────────────────────────┐
│                    DATA LAYER                                       │
│  ┌─────────────────┐    ┌─────────────────────────────────────┐   │
│  │   JSON Export   │    │           REST API                  │   │
│  │   (File-based)  │◄──►│   (Self-hosted Server)             │   │
│  └─────────────────┘    └─────────────────────────────────────┘   │
└──────────────────────────────────────────────────────────────────┘
                               │
                               ▼
┌──────────────────────────────────────────────────────────────────┐
│                      EXTERNAL SERVICES                             │
│  ┌──────────────┐    ┌──────────────┐    ┌──────────────────┐    │
│  │  Scryfall    │    │   MTGJSON    │    │  EDHREC         │    │
│  │  (Card Data) │    │  (Card DB)   │    │  (Stats)        │    │
│  └──────────────┘    └──────────────┘    └──────────────────┘    │
└──────────────────────────────────────────────────────────────────┘
```

### Component Categories

#### Trackers
Tools for tracking games in real-time:
- Life totals
- Poison counters
- Commander damage
- Turn order and timing
- Game metadata

#### Statistics Engines
Tools for analyzing exported game data:
- Win rates
- Commander performance
- Pod/group statistics
- Metagame analysis

#### Deck Analyzers
Tools for deck optimization:
- Card synergy analysis
- Mana curve optimization
- Win condition identification

## Quick Start

### For Users

1. **Pick a tracker** from the [compatible tools list](./INTEGRATIONS.md)
2. **Create an account** on a compatible server (or use local export)
3. **Start tracking games** and build your statistics

### For Developers

See [CONTRIBUTING.md](./CONTRIBUTING.md) for how to:
- Add support for the standard format
- Build new components
- Contribute to existing projects

## Data Standard

All tools in this ecosystem use a standardized JSON format for game data. See [DATA_SCHEMA.md](./DATA_SCHEMA.md) for the complete specification.

## Architecture Decisions

We document significant decisions in [ADR/](./ADR/) (Architecture Decision Records):
- Why modular design?
- Why JSON over other formats?
- REST vs GraphQL?

## License

This ecosystem specification is released under [CC0 1.0](./LICENSE) - public domain dedication. Individual tools may use different licenses.

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) for:
- How to propose new components
- How to add integrations
- Coding standards
- Review process

## Related Projects

- [EDH-Rec](https://www.edhrec.com/) - Commander recommendations
- [Scryfall](https://scryfall.com/) - Card data API
- [MTGJSON](https://mtgjson.com/) - Comprehensive card database
- [EDH Top 16](https://edhtop16.com/) - Tournament analytics
