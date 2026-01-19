# Card System, Karma Intent & Balance README

This repository defines the **card system, karma intent, and balance philosophy**
used in the game demo.

All card data (stats, elixir, rarity, karma) is defined in a single source-of-truth
spreadsheet and consumed by gameplay systems.



## Card Philosophy

The card system follows a strict normalization rule:

 **Cards with the same elixir cost share the same base stats.**

This is visible directly in the card data table:
- All 3-elixir cards share identical health, damage, cooldown, and range
- All 5-elixir cards share identical stats
- Spells and spirits follow the same elixir normalization (with health = 0 for spells)

### Why this approach?
- Prevents hidden overpowered cards
- Makes balance transparent and explainable
- Simplifies iteration during demo development
- Forces differentiation through intent and behavior instead of raw numbers

Card identity comes from:
- Card Type (Troop / Champion / Spell / Spirit / Building)
- Karma intent
- Battlefield usage


## Karma Logic

Each card is assigned **one karma intent** based on how it is meant to be used,
not based on stat strength.

Karma does **not** modify base stats.
It defines **behavioral consumption** on the battlefield.

### Karma Types

**Aggressive**
- Push-focused cards
- Designed to apply pressure
- Often require proactive play
- Examples from data: Rakshasa Warrior, Agni Bana, Ravana

**Defensive**
- Area control or protection-focused cards
- Designed to delay or deny enemy actions
- Examples from data: Vanara Sentry, Vayu Rodha, Hima Atma

**Disciplined**
- Stable, predictable value
- Core cards for structured play
- Examples from data: Vanara Archers, Hanuman, Shara Varsha

**Risk**
- High variance cards
- Strong upside with positional or timing risk
- Examples from data: Yuvaraja, Preta Laghu, Bali



## Balance Decisions

### Elixir-Based Normalization

All balance decisions start from elixir cost.

The spreadsheet clearly shows:
- Same elixir → same stats
- No stat inflation based on rarity
- Champions do not gain extra raw power by default

This ensures balance clarity during demo testing.

### Rarity Usage

Rarity is **not used to scale power**.

Rarity exists only for:
- Progression pacing
- Reward distribution
- Unlock hierarchy
- UI emphasis

Example:
A Legendary or Hero card feels special because of **identity and karma behavior**,
not because it breaks stat rules.


## Demo Readiness

For the demo build:
- Card stats are locked and normalized
- Karma intent is readable and intentional
- Final tuning happens only after battlefield validation

This allows the team to test:
- Whether stat normalization feels correct
- Whether karma intent is clearly expressed in gameplay


## Ownership & Integration

This system owns:
- Card definitions
- Elixir-based stat normalization
- Karma intent tagging
- Balance philosophy

Other systems consume this data:
- Battlefield gameplay (behavior & targeting)
- Progression & rewards
- UI visibility

Stat values are not redefined outside this system.
