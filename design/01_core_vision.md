# Core Gameplay Loop & Vision

## 1. Vision Statement

**Title:** *Untitled Colony Grand Strategy* (Fork of OpenFront.io)

**Concept:**
Transition OpenFront.io from a fast-paced, unit-spamming RTS (IO style) into a slower-paced, complex **Colony Builder / Grand Strategy Hybrid**. The game will focus on managing a nation's economy, population, and infrastructure across a persistent or long-running map, inspired by Paradox Interactive titles (Victoria, Hearts of Iron) and colony sims (RimWorld, Factorio).

**Core Pillars:**
1.  **Macro-Management over Micro-Combat**: Shift focus from moving individual units to managing supply lines, production chains, and societal needs.
2.  **Territory Matters**: Land is not just for painting the map. Each tile/province has resources, population, and terrain modifiers that dictate its strategic value.
3.  **Long-Term Strategy**: Games last hours or days, not minutes. Decisions (building a factory, enacting a policy) have long-term consequences.
4.  **Complex Economy**: Money is not the only resource. You need Food, Energy, Raw Materials (Iron, Oil), and Consumer Goods.

---

## 2. Core Gameplay Loop

The loop moves from the second-to-second "Click to Conquer" to a Minute-to-Minute "Plan and Grow".

### Phase 1: Exploration & Expansion (Early Game)
*   **Start**: Player starts with a single "Colony Ship" or "Settler Group" on a procedurally generated map.
*   **Settle**: Found a Capital City. This claims a radius of territory (Provinces).
*   **Survive**: Establish basic resource extraction (Food for population, Wood/Stone for construction).
*   **Scout**: Send scouts to identify resource deposits (Iron, Coal) and other factions (AI or Players).

### Phase 2: Exploitation & Development (Mid Game)
*   **Economy Building**: Construct specialised buildings.
    *   *Farms* -> Food (Population Growth)
    *   *Mines* -> Ores (Construction/Industry)
    *   *Factories* -> Process Ores into Goods/Weapons.
*   **Logistics**: Connect provinces via Roads and Rails (leveraging existing Rail system). Goods must physically travel or be abstracted via supply efficiency.
*   **Population Management**: Manage Workforce. Unhappy pops work less or rebel.
*   **Diplomacy**: Sign trade deals, non-aggression pacts, or form defensive leagues.

### Phase 3: Extermination & Hegemony (Late Game)
*   **Warfare**: Armies are raised from Population and equipped with stockpiled Weapons. War is expensive and hurts the economy.
*   **Technology**: Unlock advanced buildings (Nuclear Power, Advanced Manufactories) and doctrines.
*   **Victory**: achieved via:
    *   **Economic Dominance**: Control X% of global GDP.
    *   **Diplomatic Victory**: Be voted leader of the Global Federation.
    *   **Conquest**: Traditional map painting (but harder due to occupation mechanics).

---

## 3. Key Differences from OpenFront

| Feature | OpenFront (Current) | New Direction |
| :--- | :--- | :--- |
| **Pacing** | Fast (Ticks ~100ms) | Slow (Ticks ~1s, Days pass) |
| **Resources** | Gold, Troops | Food, Energy, Materials, Manpower, Money |
| **Units** | Spammable, direct control | Expensive, organized into "Divisions" or "Fleets" |
| **Territory** | Tile-based painting | Province-based (groups of tiles) or Tile-rich data |
| **Combat** | Simple numbers game | Frontlines, Morale, Equipment, Supply |
| **Persistence** | Session based | Persistent Server or Long Sessions |

---

## 4. Immediate Goals

1.  **Slow Down the Engine**: Modify the game loop tick rate.
2.  **Implement Resource System**: Replace `Gold` with a `Resources` object (Food, Wood, Iron).
3.  **Entity-Component Shift**: Allow tiles to hold complex "Buildings" (Entities) rather than just a unit type ID.
