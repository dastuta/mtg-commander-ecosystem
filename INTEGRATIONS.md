# Compatible Tools & Integrations

This document lists tools that are compatible with or can be integrated into the MTG Commander Ecosystem.

## Tracking Tools

### Native Support (JSON Export)

Tools that natively support the standard game data format:

| Tool | Export | Import | Notes |
|------|--------|--------|-------|
| [Game Tracker](https://github.com/dastuta/game-tracker) | ✅ (JSON) | ❌ | PWA, Lit/Web Components, MIT License |
| *Your Project Here* | ✅ | ✅ | Template/example |

*Submit a PR to add your tool!*

### Third-Party Tools

Tools that could be integrated or extended:

| Tool | Type | API | Notes |
|------|------|-----|-------|
| [SpellCounter](https://github.com/seanKenkeremath/SpellCounter) | Android App | ❌ | Open source, could add export |
| [EDH Tracker](https://github.com/odevine/edh-tracker) | Web App | REST | AWS backend, export possible |
| [cmdrTracker](https://github.com/GuySchnidrig/cmdrtracker) | Android App | ❌ | Open source Android app |
| [Moxfield](https://moxfield.com) | Deck Builder | ✅ | Public deck URLs, no game tracking |

## Statistics & Analysis Tools

### Existing Tools

| Tool | Focus | Open Source | Data Source |
|------|-------|-------------|-------------|
| [EDH Top 16](https://github.com/EDH-Top-16/edhtop16-v2) | Tournament stats | ✅ | TopDeck.gg |
| [EDHStats](https://github.com/goosescout/EDHStats) | Commander stats | ✅ | Custom collection |
| [Cardcognition](https://github.com/reecevela/cardcognition) | Deck optimization | ❌ | Web-based |
| [cEDH Analytics](https://github.com/cococov/cedh-analytics) | Metagame analysis | ✅ | Multiple sources |

### Desired Tools

- [ ] Player win rate calculator
- [ ] Commander performance tracker
- [ ] Pod/group statistics dashboard
- [ ] Turn-by-turn analysis

## External APIs

### Card Data

| Service | Description | API Type | License |
|---------|-------------|----------|---------|
| [Scryfall](https://scryfall.com/docs/api) | Card search & data | REST | CC BY-SA 4.0 |
| [MTGJSON](https://mtgjson.com/) | Comprehensive card DB | Download | ODC-ODbL |
| [EDHREC](https://edhrec.com/pages/api) | Commander stats | REST | Non-commercial |

### Utilities

| Service | Description | Language |
|---------|-------------|----------|
| [mtg-json-tools](https://github.com/the-muppet2/mtg-json-tools) | Python MTG data analysis | Python |
| [mtg-scripting-toolkit](https://github.com/ahmattox/mtg-scripting-toolkit) | TypeScript MTG tools | TypeScript |
| [mtg-deckstats](https://github.com/lheyberger/mtg-deckstats) | Deck statistics | Python |

## Deck Building Sites

These sites provide deck data that could be imported:

| Site | Export Format | API | Notes |
|------|-------------|-----|-------|
| Moxfield | JSON, CSV | Partial | Public decks |
| Archidekt | JSON | ✅ | Public decks |
| Deckstats | CSV | ❌ | Requires login |
| TappedOut | CSV, TappedOut format | ❌ | Historical |
| Aetherhub | JSON | ✅ | Some features require login |

## Backend Solutions

### Self-Hosted

| Solution | Stack | Complexity | Notes |
|----------|-------|-----------|-------|
| *Reference Implementation* | Node.js + PostgreSQL | Medium | To be built |
| [Supabase](https://supabase.com/) | PostgreSQL + Auth | Low | Managed service |
| [PocketBase](https://pocketbase.io/) | SQLite + Auth | Low | Single binary |

### Cloud Services

| Service | Notes |
|---------|-------|
| Railway | Easy deployment, paid |
| Render | Free tier available |
| Fly.io | Good for containers |
| DigitalOcean App Platform | Simple deployment |

## Contributing

To add a tool to this list:

1. Fork the repository
2. Add your tool to the appropriate section
3. Include: name, link, description, and compatibility status
4. Submit a pull request

Format:
```markdown
| [Tool Name](URL) | Type | Status | Notes |
```
