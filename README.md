# MTG Commander Ecosystem

> **An open, modular ecosystem for Magic: The Gathering Commander tracking, statistics, and deck analysis.**

---

## ⚠️ IMPORTANT DISCLAIMER - PLEASE READ

### Community-Driven, Non-Profit Project

This project is **100% community-driven** and **non-profit**. We are a group of Magic: The Gathering players who want to create open-source tools for the community. There is:

- **No commercial interest** - We don't make money from this
- **No advertising** - We don't sell your data or show ads
- **No company backing** - This is maintained by volunteers in their free time
- **No obligation** - Use it as you wish, contribute if you want

### 🚧 In Development / Conceptual Phase

**This project is currently in the PLANNING PHASE.**

What exists right now:
- ✅ This documentation repository
- ✅ Conceptual specifications
- ✅ Proposed data formats
- ✅ Architecture discussions

What does NOT exist yet:
- ❌ No working application
- ❌ No deployed server
- ❌ No finished product

This repository serves as a **planning and coordination space** for the community to discuss, design, and eventually build the ecosystem together. Nothing here is final, and nothing is guaranteed to work.

### Everyone is Welcome to Contribute

We explicitly welcome:

- **Feedback** - Tell us what features you need
- **Criticism** - Point out flaws in our thinking
- **Ideas** - Suggest new approaches or components
- **Contributions** - Help design, code, or document
- **Questions** - If something is unclear, ask!

No MTG knowledge required - we need developers, designers, writers, and players alike.

**Open an [Issue](../issues) or [Discussion](../discussions) to get involved!**

---

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

## Current Status

| Area | Status | Notes |
|------|--------|-------|
| Data Schema | 🟡 Draft | First version proposed |
| Architecture | 🟡 Draft | General concept agreed |
| Documentation | 🟡 Draft | This repository |
| Tracker App | ⬜ Not Started | Needs implementation |
| Statistics Engine | ⬜ Not Started | Needs implementation |
| Server | ⬜ Not Started | Needs implementation |
| Deck Analyzer | ⬜ Not Started | Future consideration |

### Legend
- 🟢 Complete
- 🟡 In Progress / Draft
- ⬜ Not Started

## How to Get Involved

### For Players
1. **Share your needs** - What features would you want?
2. **Give feedback** - Is the proposed data format missing something?
3. **Spread the word** - Share this with fellow EDH players

### For Developers
1. **Review the specs** - Does the architecture make sense?
2. **Build a prototype** - Try implementing a component
3. **Contribute code** - See [CONTRIBUTING.md](./CONTRIBUTING.md)

### For Everyone
1. **Open a Discussion** - Introduce yourself, share ideas
2. **Create an Issue** - Report problems or request features
3. **Ask Questions** - Nothing is too basic to ask

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
