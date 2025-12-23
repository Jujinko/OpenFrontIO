# Map & Territory System

## 1. The Province Concept

In OpenFront, every tile is an island. In "Paradox" games, the atomic unit of gameplay is the **Province** (a named region consisting of multiple pixels/tiles).

### Implementation
*   **Tilemap**: Remains the visual and movement layer. 2000x2000 grid.
*   **ProvinceMap**: An overlay.
    *   **Generation**: During map gen, use a Voronoi diagram or Flood Fill algorithm to group land tiles into ~50-200 tile clusters.
    *   **Data**:
        *   `id`: Unique Int.
        *   `name`: String (Procedurally generated: "New London", "Sector 7").
        *   `terrain_features`: Forest, Desert, Mountain (Aggregate of tile terrains).
        *   `owner`: Reference to Player (Provinces change hands as a whole, usually).
        *   `center`: `TileRef` (For UI labels and army snapping).

### 2. Territory Control

**Current System**: "Paint the map". Move unit to tile -> Tile is yours.
**New System**: **Province Occupation**.

1.  **Claims**: You build a "City" or "Outpost" in a Province to claim it. The whole province turns your color.
2.  **Contesting**: Enemy armies enter the province. They don't flip tiles instantly.
3.  **Siege/Occupation**:
    *   Enemy units must "Siege" the Province Center (City).
    *   Siege progress bar based on `(Attacker Attack - Defender Fortification)`.
    *   Once the City falls, the Province control flips (or becomes "Occupied").

### 3. Terrain & Resources

We need to make geography matter.

**Resource Nodes**:
*   Instead of generic production, specific tiles contain **Resource Nodes**.
    *   *Iron Vein*: Can build `Mine`.
    *   *Fertile Soil*: Bonus to `Farm` output.
    *   *Oil Field*: Can build `Pumpjack`.
*   These nodes should be visible on the map.

**Terrain Modifiers**:
*   **Forest**: -20% Movement Speed, +10% Defense. High Wood output.
*   **Mountain**: Impassable for Tanks, +50% Defense. High Stone/Iron output.
*   **River**: Major defensive bonus if attacking across. Trade bonus if controlling the river.

### 4. The Map Generator Update

The Go-based `map-generator` needs to be updated or post-processed:
1.  **Region Identification**: Algorithm to generate the Province ID layer.
2.  **Resource Scattering**: Algorithm to place Resource Nodes based on logic (e.g., Oil near water/deserts, Iron in mountains).
3.  **Navigable Rivers**: Ensure rivers are wide enough for trade ships or have bridges.

### 5. Fog of War

*   **Current**: View radius around units.
*   **New**:
    *   **Explored vs Unexplored**: Black map until scouted.
    *   **Visible vs Fog**: Once explored, you see terrain but not units unless you have active vision.
    *   **Intel**: You might see "Enemy Activity" icons in a province without seeing exact unit counts if you have low Intel.
