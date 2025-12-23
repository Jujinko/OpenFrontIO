# Economy & Resource Management

## 1. The Core Loop: Extract -> Process -> Consume

The economy will drive the gameplay. You cannot build a tank with just gold; you need Steel and Fuel.

### Primary Resources (Raw)
1.  **Food**: Consumed by Population. Sources: Farms, Fishing, Hunting.
2.  **Wood**: Early construction. Sources: Forests.
3.  **Stone**: Early construction, Forts. Sources: Quarries.
4.  **Iron Ore**: Processed into Steel. Sources: Mines.
5.  **Oil**: Processed into Fuel. Sources: Oil Wells.

### Secondary Resources (Processed)
1.  **Steel**: Made from Iron + Coal (or generic fuel). Used for Industry/Weapons.
2.  **Fuel**: Made from Oil. Used for Tanks/Ships/Planes.
3.  **Consumer Goods**: Made from various raw materials. Consumed by Population for Happiness.
4.  **Weapons/Munitions**: Consumed by Armies.

### Tertiary Resources (Abstract)
1.  **Manpower**: The number of able-bodied recruits. Drains when training units. Recovers slowly based on Population.
2.  **Energy**: Power grid capacity. Required for Factories.
3.  **Money/Gold**: Used for trade, upkeep, and rushing construction.

---

## 2. Population Mechanics

Every Province has a **Population** count.
*   **Strata**:
    *   *Workers*: Basic labor (Farms, Mines).
    *   *Specialists*: Advanced labor (Factories, Research).
    *   *Soldiers*: Manpower pool.
*   **Needs**:
    *   Food (Survival).
    *   Goods (Happiness).
*   **Growth**: Positive if Food > Demand.
*   **Migration**: Pops move to provinces with Jobs and Happiness.

---

## 3. Production & Buildings

Buildings are the engines of the economy.

**Construction Queue**:
*   Players queue buildings in a Province.
*   Cost: deducted upfront or streamed (requiring flow of Materials).
*   Time: Based on "Construction Industry" level.

**Building Types**:
*   *House*: Increases Pop Cap.
*   *Farm*: Produces Food.
*   *Smelter*: Converts Iron -> Steel.
*   *Factory*: Converts Steel -> Weapons.
*   *Logistics Hub*: Increases supply range.

---

## 4. Supply Lines

This is a critical "Paradox-like" feature.
*   **Stockpiles**: Resources are stored in **Cities/Warehouses**.
*   **Flow**:
    *   A Farm in Province A produces Food.
    *   The City in Province B needs Food.
    *   There must be a path (Road/Rail/River) between A and B.
*   **Army Supply**:
    *   Armies carry a buffer of Food/Fuel/Ammo.
    *   They replenish from the nearest friendly Warehouse within range.
    *   If cut off (encircled), they suffer heavy attrition.

---

## 5. Trade & Market

*   **Global Market**: Players can sell excess resources for Gold and buy shortages.
*   **Prices**: Dynamic based on Supply/Demand.
*   **Private Trade**: Direct deals between allied players (e.g., "I give you 100 Oil/month, you give me 50 Steel/month").
