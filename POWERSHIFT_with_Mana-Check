### Druid Powershift / Reshift Macros (Vanilla 1.12 / Turtle WoW)

**Prerequisites:**

* **[SuperWoW](https://github.com/balakethelock/SuperWoW)** (Required for both Energy and Mana checks in Cat Form)
* **[SuperCleveRoidMacros](https://github.com/jrc13245/SuperCleveRoidMacros)** (Recommended for extended conditionals)

---

#### 1. Modern "Reshift" Approach (Recommended)

*Requires the custom `Reshift` spell (Turtle WoW).*

**Option A: Simple (Energy Check Only)**
*Best for pure DPS who don't worry about running OOM.*

```lua
/cast [myrawpower:<=10] Reshift

```

* **Note:** Requires SuperCleveRoidMacros.

**Option B: Safe (Energy + Mana Safety Check)**
*Best for Hybrids/PvP. Checks Energy **AND** hidden Caster Mana. Prevents shifting out if you fall below a specific Mana %.*

```lua
/run local E=14 local P=50 local c,m=UnitMana("player") local _,mm=UnitManaMax("player") if c<=E and (m/mm)>(P/100) then CastSpellByName("Reshift") end

```

* **E=14**: The Energy threshold (Shifts if Energy is 14 or lower).
* **P=50**: The Safety threshold (Stops shifting if Mana is below 50%).
* **Note:** Works natively with SuperWoW (no specific macro addon required).

---

#### 2. Legacy Approach (DruidManaLib)

*Deprecated. Use this only if you cannot use SuperWoW or the Reshift spell.*

```lua
/script PowershiftSave()

function PowershiftSave()
    if not DruidManaLib then return end
    
    local currentForm = UnitPowerType("player")
    local actualMana = DruidManaLib:GetMana()
    local catFormCost = 304  -- Your cat form mana cost
    
    if currentForm == 3 then
        -- Only powershift if we have enough mana to shift back
        if actualMana >= catFormCost then
            cast("Cat Form")
        end
    elseif currentForm == 0 then
        if actualMana >= catFormCost then
            cast("Cat Form")
        end
    end
end

```
