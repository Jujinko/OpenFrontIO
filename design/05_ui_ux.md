# UI/UX Overhaul

## 1. Design Philosophy

**From Action to Information.**
OpenFront's UI is minimal to maximize view of the battlefield. The new UI must be **Data-Rich**. Players need to see resource graphs, demographic charts, production efficiency, and political maps.

## 2. Key UI Components

### A. The Top Bar (Macro Status)
Always visible.
*   **Resources**: Icons + Current Stock + (+/- Net Change).
    *   *Tooltip*: Breakdown of Income/Expense.
*   **Date/Time**: Current Date, Speed Controls (Pause, 1x, 2x, 3x).
*   **Alerts**: Notification flags (Low Food, Research Complete, Diplomatic Offer).

### B. The Sidebar / Action Panel (Context Sensitive)
When clicking an object, this panel populates.

*   **Province View**:
    *   Name, Terrain Image, Population.
    *   **Building Slots**: Grid showing current buildings. Click to upgrade/demolish.
    *   **Production Queue**: List of items being built.
*   **Army View**:
    *   General portrait.
    *   Composition (Infantry, Tanks, Artillery).
    *   Stats (Soft Attack, Hard Attack, Organization, Supply).
    *   Actions (Split, Merge, Patrol, Entrench).

### C. Map Modes
Crucial for strategy games. Toggle buttons to color the map differently.
1.  **Political**: Standard view (Nation Colors).
2.  **Resource**: Highlights deposits (Iron = Red, Oil = Black).
3.  **Terrain**: Shows impassable mountains, forests.
4.  **Supply**: Green (Good supply) to Red (Starving).
5.  **Unrest/Happiness**: Heatmap of rebellious provinces.

### D. Full Screen Windows (Management)
*   **Economy Tab**: Adjust tax rates, view global production graphs.
*   **Research Tree**: Tech web to unlock new units/buildings.
*   **Diplomacy**: List of nations, relations, treaty options.
*   **Military**: Army organizer, template designer (Design your Division composition).

---

## 3. Technology & Implementation

*   **Lit (Web Components)**: Continue using Lit as it's already in the project. It's efficient and modular.
*   **Windowing System**: Create a generic `<draggable-window>` component for the management screens.
*   **Data Binding**: Need a robust way to listen to game state updates.
    *   Observer pattern on the Client Game State.
    *   When `GameState.resources.food` changes, the Top Bar updates automatically.

## 4. Visual Style

*   **Aesthetic**: "Industrial/Clean". Dark backgrounds, sharp borders, high-contrast text.
*   **Iconography**: Use clear, distinct icons for every resource and unit. (SVG).
*   **Fonts**: Legible sans-serif for UI, maybe serif for titles/province names.

## 5. Input Changes

*   **Selection**: Box select for armies is fine. Single click for Provinces.
*   **Right Click**: Context menu (Move here, Attack, Trade with owner).
*   **Zoom**: Mouse wheel. Smooth transition from "Paper Map" (far) to "Satellite View" (close).
