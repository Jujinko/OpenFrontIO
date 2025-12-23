# Project Management & Roadmap

**Last Updated:** (Initial Creation)
**Current Phase:** Phase 0 - Foundation & Design

## 1. Current Status
*   **Active Goal:** Setting up the project structure and design documentation.
*   **Recent Accomplishments:**
    *   Created core design documents (Vision, Architecture, Map, Economy, UI).
    *   Established Agent Instructions.
*   **Next Immediate Step:** Begin Phase 1 (Technical Foundation).

---

## 2. Short-Term Goals (Phase 1: Technical Foundation)
*Focus: Refactoring the engine to support the new scale and data requirements.*

- [ ] **Task 1.1: Slow Down the Loop**
    - [ ] Decouple `GameTick` (Logic) from `RenderTick`.
    - [ ] Implement a generic "Day/Month" cycle timer.
- [ ] **Task 1.2: Resource System Implementation**
    - [ ] Create `ResourceContainer` class/interface.
    - [ ] Refactor `Player` to use `ResourceContainer` instead of `gold`/`troops`.
    - [ ] Add basic resource types: Food, Wood, Stone, Iron, Oil.
- [ ] **Task 1.3: Province System Prototype**
    - [ ] Create `ProvinceID` type.
    - [ ] Update `GameMap` to store `Tile -> Province` mapping.
    - [ ] Implement a simple visual debug mode to see Province boundaries.

## 3. Medium-Term Goals (Phase 2: Gameplay Loop)
*Focus: Implementing the "Extract -> Process -> Consume" loop.*

- [ ] **Task 2.1: Entities & Buildings**
    - [ ] Create `Structure` entity separated from `Unit`.
    - [ ] Implement `Farm` and `Mine` structures.
- [ ] **Task 2.2: Economy Tick**
    - [ ] Implement the `EconomyTick` function (runs once per "Day").
    - [ ] Calculate production (Buildings -> Output) and consumption (Pop -> Food).
- [ ] **Task 2.3: Basic UI**
    - [ ] Replace the top bar with a Resource Dashboard.
    - [ ] Create a "Province Inspector" sidebar.

## 4. Long-Term Goals (Phase 3: The "Game")
*Focus: AI, Diplomacy, and Polish.*

- [ ] **Task 3.1: AI Overhaul**
    - [ ] Create an "Economy Manager" for AI (decides what to build).
    - [ ] Create a "Frontline Manager" for AI (decides where to move armies).
- [ ] **Task 3.2: Save/Load System**
    - [ ] Serialize `GameMap` and `Entity` state to JSON/Binary.
    - [ ] Implement database persistence.
- [ ] **Task 3.3: Visual Polish**
    - [ ] New sprites for structures.
    - [ ] Map modes (Political, Terrain, Resource).

---

## 5. Task Backlog (Unsorted Ideas)
*   [ ] River navigation mechanics.
*   [ ] "Manpower" as a resource vs "Population" as a stat.
*   [ ] Tech tree implementation.
*   [ ] Fog of War update (Intel system).
