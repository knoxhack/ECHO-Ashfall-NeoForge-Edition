# Ashfall UX / Game Parity Spec

## Goal
Ashfall must feel like the same game across NeoForge, Native, Standalone Runtime, and Standalone Engine, with the same module-driven menus, HUDs, inventory, keys, overlays, terminal, index, and gameplay contracts.

**Core rule:** No runtime owns the player-facing truth. Every menu, HUD, overlay, keybind, and gameplay contract is defined once in `ECHO-Modules` and adapted by each runtime lane.

## Reference Lane
The NeoForge Ashfall Edition is the reference lane. It ships the full set of `neoforge` artifact-family modules and exercises the ScreenCore, ThemeCore, InputCore, HUDCore, Terminal, Index, Lens, and Ashfall content modules in a real Minecraft client.

## Current Standalone Engine Baseline
The Standalone Engine (`ECHO-Standalone-Engine`) is a Java 21 clean-room runtime. It currently implements:
- Strict module graph loading with SHA-256 verification.
- A software voxel renderer and player controller.
- Hardcoded title screen, pause screen, in-game HUD, and world flow.
- Survival vitals, block interaction, inventory hotbar, crafting, entities, and save/reload.

It does **not** yet consume the shared ScreenCore/EUI contracts. Its UI is hardcoded in `HudRenderer` and `GameClient`, not driven by `echoscreencore`/`echohudcore`/`echothemecore`/`echoinputcore`.

## Missing Player-Facing Systems

| System | Reference (NeoForge) | Engine Status | Required For |
|---|---|---|---|
| Main menu (`ashfall:title`) | ScreenCore `echoscreencore` page with themed buttons | Hardcoded text prompts | Beta |
| Pause menu (`ashfall:pause`) | ScreenCore overlay with Resume/Save/Settings/Quit | Hardcoded text prompts | Beta |
| Inventory (`ashfall:inventory`) | `echoindex:inventory_overlay` + ScreenCore grid | Hotbar only; no full inventory screen | Beta |
| Crafting (`ashfall:crafting`) | `echorecipecore` + `echostationcore` recipes | 4 hardcoded recipes | Beta |
| Stations (`ashfall:station`) | `echostationcore` station UIs | No station UI | RC |
| HUD (`ashfall:hud`) | `echohudcore` widgets/tracker/compass/hazard | Hardcoded bars | Beta |
| Lens (`ashfall:lens`) | `echolens:field_lens` overlay | No lens | RC |
| Index (`ashfall:index`) | `echoindex:index_dashboard` | No index | RC |
| Terminal (`ashfall:terminal`) | `echoterminal:terminal_overview` | Simple text prompt only | RC |
| Settings (`ashfall:settings`) | ScreenCore settings page | None | RC |
| Keybinds (`ashfall:keybinds`) | `echoinputcore` contexts/bindings | Hardcoded WASD + mouse | Beta |
| World flow (`ashfall:world_flow`) | New/load world screens with metadata | New/continue via key presses | Beta |
| Death/respawn (`ashfall:death`) | Death screen + respawn logic | No death screen | RC |
| Module diagnostics (`ashfall:modules`) | Module status / diagnostics screen | None | RC |

## Parity Matrix

| Feature | NeoForge | Native | Standalone Runtime | Standalone Engine |
|---|---|---|---|---|
| Main menu | ✅ ScreenCore | ✅ | ✅ | ❌ hardcoded |
| Pause menu | ✅ ScreenCore | ✅ | ✅ | ❌ hardcoded |
| Inventory screen | ✅ `echoindex` | ✅ | ⚠️ | ❌ |
| Crafting | ✅ `echorecipecore` | ✅ | ⚠️ | ⚠️ hardcoded |
| Stations | ✅ `echostationcore` | ✅ | ⚠️ | ❌ |
| HUD | ✅ `echohudcore` | ✅ | ✅ | ⚠️ hardcoded |
| Lens | ✅ `echolens` | ✅ | ⚠️ | ❌ |
| Index | ✅ `echoindex` | ✅ | ⚠️ | ❌ |
| Terminal | ✅ `echoterminal` | ✅ | ✅ | ⚠️ minimal |
| Settings | ✅ ScreenCore | ✅ | ⚠️ | ❌ |
| Keybinds | ✅ `echoinputcore` | ✅ | ✅ | ⚠️ hardcoded |
| World flow | ✅ ScreenCore | ✅ | ✅ | ⚠️ minimal |
| Death/respawn | ✅ | ✅ | ✅ | ❌ |
| Module diagnostics | ✅ | ✅ | ⚠️ | ❌ |

Legend: ✅ complete, ⚠️ partial, ❌ missing.

## Classification

### Required for Beta
- Main menu and pause menu rendered through shared ScreenCore runtime.
- Basic keybind/input contract consumption.
- Player inventory screen with drag/drop and persistence.
- Basic crafting through `echorecipecore` contracts.
- HUD driven by `echohudcore` contracts (health, food, water, hazard, hotbar).
- New/load world flow with save metadata and version warnings.

### Required for RC
- Stations via `echostationcore`.
- Terminal via `echoterminal`.
- Index via `echoindex`.
- Lens via `echolens`.
- Settings screen.
- Death/respawn flow.
- Module diagnostics screen.

### Later
- Full visual theme parity via `echothemecore`.
- Advanced accessibility settings.
- Rich animation and particle parity.

## Module Contract Surface

The Engine must consume these module-provided contracts:

- `echoscreencore` — `screen.surface`, `screen.components`, `screen.layouts`, `screen.style`, `screen.actions`, `screen.bindings`.
- `echothemecore` — `theme.tokens`, `theme.ui_skins`, `theme.cyberglass`.
- `echoinputcore` — `input.contexts`, `input.keybind_registry`.
- `echohudcore` — `hud.widgets`, `hud.hazard_meters`, `hud.mission_tracker`, `hud.compass_indicators`.
- `echoterminal` — `terminal.surface`.
- `echoindex` — `index.recipes`, `index.inventory_overlay`.
- `echolens` — `lens.scanners`.
- `echostationcore` — `foundation.stations`, `foundation.shared_recipe_surfaces`.
- `echorecipecore` — `recipes.backend`, `recipes.machine_views`, `recipes.search`.
- `echohealthcore` — `runtime.health`.
- `echocreaturecore` — `creature.archetypes`, `creature.ai_profiles`.
- `echocombatcore` — `combat.damage`, `combat.weapon_traits`.
- `echostatuscore` — `status.effects`, `status.exposure`.

## Common Screen IDs

See `docs/ui/screen-ids.md` for the canonical screen ID catalog and mappings to existing module page IDs.
