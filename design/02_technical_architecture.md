# Technical Architecture & Refactoring

## 1. Current State Analysis

*   **Language**: TypeScript (Front & Back).
*   **Networking**: WebSockets, custom binary protocol (PatternDecoder/Schemas).
*   **State Management**:
    *   `GameMap.ts`: Packed binary arrays (`Uint16Array`, `Uint8Array`) for high performance.
    *   `Game.ts`: Central God-object managing everything.
    *   `Unit.ts`: OOP classes for units.
*   **Renderer**: PIXI.js.
*   **Map Generation**: Go-based binary generator.

## 2. Refactoring Needs

To support the "Colony/Paradox" vision, we need to store *more data* than the current packed arrays allow. The current `GameMap` is optimized for millions of tiles with minimal state (Owner, Terrain, Defense). We need Inventory, Population, and Building State per tile (or province).

### A. The Hybrid Data Model

We cannot store complex objects for every single tile in a 2000x2000 map (4M objects) without blowing up memory.

**Proposal: "Provinces" & "Active Entities"**
1.  **Tiles (Base Layer)**: Keep the efficient `Uint16Array` for terrain and raw ownership.
2.  **Provinces (Logical Layer)**:
    *   Map a group of tiles (e.g., Voronoi regions or 10x10 chunks) to a single `ProvinceID`.
    *   `Province` object stores: `Population`, `Resources`, `LocalMarket`.
    *   Map `TileID -> ProvinceID` via a lookup array.
3.  **Structures (Entities)**:
    *   Buildings are sparse. Only ~1-5% of tiles will have a building.
    *   Use a `Map<TileRef, Structure>` to store building data (Type, Level, Inventory, WorkerCount).
    *   This avoids allocating objects for empty tiles.

### B. Game Loop & Tick System

*   **Current**: High frequency ticks (likely 10-20 TPS).
*   **New**:
    *   **Logic Tick**: 1-5 TPS. Handles movement, combat.
    *   **Economy Tick**: Once per "Day" (e.g., every 10-30 Logic Ticks). Handles resource production, consumption, growth.
    *   Decoupling these prevents lag as the economy grows complex.

### C. Resource System (ECS-lite)

Instead of hardcoding `Gold` and `Troops` in `Player.ts`, we implement a generic Resource Container.

```typescript
type ResourceType = 'Food' | 'Wood' | 'Iron' | 'Gold' | 'Manpower';

interface ResourceContainer {
    storage: Record<ResourceType, number>;
    capacity: Record<ResourceType, number>;
    // Helpers
    add(type: ResourceType, amount: number): void;
    remove(type: ResourceType, amount: number): boolean;
}
```

This should be attached to `Player` (Global Stockpile) and `Structure` (Local Buffer).

### D. Networking Updates

The current `GameUpdates.ts` sends highly optimized diffs.
We need to extend the Schema (`Schemas.ts`, `ApiSchemas.ts`) to support:
1.  **Detailed Entity Updates**: Sending full building info when clicking on a province.
2.  **Resource Flows**: Updates on income/expenses (not every tick, maybe polled or batched).

### E. Persistence

*   **Current**: In-memory.
*   **New**: Periodic dumps to Database (Postgres/SQLite) or JSON file serialization for "Save/Load" functionality, essential for long games.

---

## 3. Tech Stack Changes

*   **Backend**: Keep Node.js. Consider moving heavy calculation (Pathfinding/Economy) to `Worker` threads if it bottlenecks.
*   **Frontend**:
    *   Keep PIXI.js for the map.
    *   Heavy UI lift: The current HTML/Lit UI is fine, but we will need *many* more windows (Graphs, Tables).

---

## 4. Migration Plan

1.  **Step 1**: Abstract `Player.gold` into `Player.resources`.
2.  **Step 2**: Create `ProvinceManager` to group tiles.
3.  **Step 3**: Refactor `Unit` system to separate `MobileUnits` (Armies) from `StaticStructure` (Buildings).
4.  **Step 4**: Implement the Economy Tick loop.
