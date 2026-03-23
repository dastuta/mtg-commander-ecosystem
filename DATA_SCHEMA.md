# MTG Commander Game Data Schema

> Standardized JSON format for game data exchange between ecosystem components.

## Version

Current version: `1.0.0`

All files MUST include a `version` field. Consumers should validate against the version to ensure compatibility.

## File Types

### Complete Game Export (`game.json`)

```json
{
  "version": "1.0.0",
  "type": "game",
  "createdAt": "2024-01-15T19:30:00Z",
  "id": "550e8400-e29b-41d4-a716-446655440000",

  "meta": {
    "format": "commander",
    "date": "2024-01-15",
    "startTime": "2024-01-15T14:00:00Z",
    "endTime": "2024-01-15T15:30:00Z",
    "duration": 5400,
    "winningPlayerId": "player-uuid-1",
    "winningReason": "last_standing",
    "winningReasonDetails": "Combat damage from Emiel",
    "groupId": "playgroup-uuid-1",
    "notes": "Great game!",
    "exportedBy": "TrackerApp v2.0"
  },

  "players": [
    {
      "id": "player-uuid-1",
      "name": "Alice",
      "seat": 1,
      "commander": {
        "name": "Emiel the Blessed",
        "scryfallId": "abc123"
      },
      "decklist": "https://moxfield.com/decks/abc",
      "isWinner": true
    },
    {
      "id": "player-uuid-2",
      "name": "Bob",
      "seat": 2,
      "commander": {
        "name": "Winota, Keeper of Force",
        "scryfallId": "def456"
      },
      "isWinner": false
    }
  ],

  "turns": [
    {
      "turnNumber": 1,
      "playerId": "player-uuid-1",
      "playerName": "Alice",
      "startTime": "2024-01-15T14:00:00Z",
      "endTime": "2024-01-15T14:05:00Z",
      "duration": 300
    }
  ],

  "actions": [
    {
      "id": "action-uuid-1",
      "turnNumber": 3,
      "timestamp": "2024-01-15T14:12:00Z",
      "type": "damage",
      "category": "life",
      "source": {
        "playerId": "player-uuid-1",
        "name": "Alice"
      },
      "target": {
        "playerId": "player-uuid-2",
        "name": "Bob"
      },
      "value": 5,
      "previousLife": 40,
      "resultingLife": 35,
      "sourceCard": "Ghalta, Primal Hunger"
    },
    {
      "id": "action-uuid-2",
      "turnNumber": 5,
      "timestamp": "2024-01-15T14:25:00Z",
      "type": "poison",
      "category": "poison",
      "source": null,
      "target": {
        "playerId": "player-uuid-3",
        "name": "Charlie"
      },
      "value": 3,
      "previousPoison": 0,
      "resultingPoison": 3
    },
    {
      "id": "action-uuid-3",
      "turnNumber": 7,
      "timestamp": "2024-01-15T14:40:00Z",
      "type": "commander_damage",
      "category": "commander",
      "source": {
        "playerId": "player-uuid-2",
        "name": "Bob"
      },
      "target": {
        "playerId": "player-uuid-1",
        "name": "Alice"
      },
      "value": 3,
      "sourceCard": "Winota, Keeper of Force",
      "totalDamageFromSource": 9,
      "previousLife": 35,
      "resultingLife": 32
    },
    {
      "id": "action-uuid-4",
      "turnNumber": 9,
      "timestamp": "2024-01-15T14:55:00Z",
      "type": "defeat",
      "category": "system",
      "target": {
        "playerId": "player-uuid-3",
        "name": "Charlie"
      },
      "reason": "poison",
      "eliminatedBy": null
    },
    {
      "id": "action-uuid-5",
      "turnNumber": 11,
      "timestamp": "2024-01-15T15:10:00Z",
      "type": "victory",
      "category": "system",
      "target": {
        "playerId": "player-uuid-1",
        "name": "Alice"
      },
      "reason": "last_standing"
    }
  ],

  "finalState": {
    "life": {
      "player-uuid-1": 28,
      "player-uuid-2": 15,
      "player-uuid-3": 0,
      "player-uuid-4": 0
    },
    "poison": {
      "player-uuid-1": 0,
      "player-uuid-2": 0,
      "player-uuid-3": 10,
      "player-uuid-4": 0
    },
    "commanderDamage": {
      "player-uuid-2-player-uuid-1": 9,
      "player-uuid-1-player-uuid-2": 12,
      "player-uuid-4-player-uuid-3": 21
    }
  },

  "defeatedPlayers": [
    {
      "playerId": "player-uuid-3",
      "playerName": "Charlie",
      "reason": "poison",
      "eliminatedBy": null,
      "turnEliminated": 9
    },
    {
      "playerId": "player-uuid-4",
      "playerName": "Diana",
      "reason": "commander_damage",
      "eliminatedBy": "player-uuid-4",
      "eliminatedByName": "Diana",
      "turnEliminated": 8
    }
  ]
}
```

### Batch Export (`games.json`)

For exporting multiple games at once:

```json
{
  "version": "1.0.0",
  "type": "batch",
  "exportedAt": "2024-01-15T20:00:00Z",
  "count": 2,
  "games": [ /* array of game objects */ ]
}
```

### Player Profile (`player.json`)

```json
{
  "version": "1.0.0",
  "type": "player",
  "id": "player-uuid-1",
  "name": "Alice",
  "createdAt": "2023-06-01T00:00:00Z",
  
  "aliases": ["Alice", "AliceK"],
  
  "commanders": [
    {
      "name": "Emiel the Blessed",
      "scryfallId": "abc123",
      "gamesPlayed": 15,
      "wins": 8
    }
  ],
  
  "playgroups": ["playgroup-uuid-1", "playgroup-uuid-2"]
}
```

### Playgroup (`playgroup.json`)

```json
{
  "version": "1.0.0",
  "type": "playgroup",
  "id": "playgroup-uuid-1",
  "name": "Thursday Night Pod",
  "createdAt": "2023-01-01T00:00:00Z",
  
  "members": [
    {
      "playerId": "player-uuid-1",
      "playerName": "Alice",
      "joinedAt": "2023-01-01T00:00:00Z"
    }
  ],
  
  "settings": {
    "defaultStartingLife": 40,
    "maxPoisonCounters": 10,
    "commanderDamageThreshold": 21
  }
}
```

## Action Types

| Type | Category | Description |
|------|----------|-------------|
| `damage` | life | Direct damage to life total |
| `heal` | life | Life gained |
| `poison` | poison | Poison counters gained |
| `commander_damage` | commander | Commander damage from a specific source |
| `defeat` | system | Player eliminated from game |
| `victory` | system | Player won the game |
| `concession` | system | Player conceded |

## Defeat Reasons

| Reason | Description |
|--------|-------------|
| `life` | Life reached 0 |
| `poison` | Poison counters reached threshold (usually 10) |
| `commander_damage` | Commander damage from one source reached threshold (usually 21) |
| `concession` | Player voluntarily left the game |
| `timeout` | Player ran out of time |
| `other` | Other reason |

## Winning Reasons

| Reason | Description |
|--------|-------------|
| `last_standing` | Only player remaining |
| `commander_damage` | Defeated all opponents via commander damage |
| `poison` | All opponents reached max poison |
| `concession` | All opponents conceded |
| `agreed` | Group agreed on winner |
| `special_effect` | Card effect (e.g., "Thassa's Oracle" win) |

## Validation

Tools SHOULD validate incoming data against this schema. Use [JSON Schema](https://json-schema.org/) for automated validation.

## Extensibility

Custom fields can be added using namespaced keys:

```json
{
  "meta": {
    "custom/myapp/feature": "value"
  }
}
```

Namespaced keys starting with `custom/` should be preserved by other tools but not required.

## Change Log

### 1.0.0
- Initial specification
- Game export format
- Player profile format
- Playgroup format
