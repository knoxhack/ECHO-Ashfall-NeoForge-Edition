# Ashfall Common Screen IDs

This catalog defines the canonical screen IDs used across all Ashfall runtime lanes. The IDs are mapped to existing `ECHO-Modules` page/overlay IDs where applicable.

## Common Screen IDs

| Canonical ID | Purpose | Module Page / Overlay Mapping |
|---|---|---|
| `ashfall:title` | Main menu (Continue, New World, Load World, Settings, Modules, Diagnostics, Quit) | `echoscreencore:reference_feature_hub` (theme shell) |
| `ashfall:pause` | Pause overlay (Resume, Save, Settings, Modules, Return To Title, Quit) | `echoscreencore:reference_modal_overlay` |
| `ashfall:inventory` | Player inventory + hotbar | `echoindex:inventory_overlay` |
| `ashfall:crafting` | Basic crafting grid / recipe surface | `echorecipecore` machine view + `echoscreencore` components |
| `ashfall:station` | Crafting station / machine UI | `echostationcore` station JSON + `echoscreencore` components |
| `ashfall:terminal` | Field Terminal | `echoterminal:terminal_overview` |
| `ashfall:index` | Item/block/encyclopedia Index | `echoindex:index_dashboard` |
| `ashfall:lens` | Scanner lens overlay | `echolens:field_lens` / `echolens:lens_overlay` |
| `ashfall:settings` | Game settings | `echoterminal:terminal_settings` or `echoscreencore:reference_settings` |
| `ashfall:modules` | Installed module diagnostics | `echoterminal:terminal_addons` / `echoscreencore:reference_dashboard` |
| `ashfall:diagnostics` | Runtime diagnostics | `echoterminal:terminal_data_core` |
| `ashfall:loading` | World loading screen | `echoscreencore:reference_workbench` |
| `ashfall:error` | Fatal error screen | `echoscreencore:reference_bad_layouts` (diagnostic shell) |
| `ashfall:death` | Death / respawn screen | `echohudcore:screen_safe_area` overlay + prompt |
| `ashfall:new_world` | New world options | `echoscreencore:reference_inputs` |
| `ashfall:load_world` | Save list | `echoscreencore:reference_dense_list` |

## Module Page Reference

### `echoscreencore`
- `echoscreencore:reference_feature_hub`
- `echoscreencore:reference_workbench`
- `echoscreencore:reference_dashboard`
- `echoscreencore:reference_list_detail`
- `echoscreencore:reference_three_column`
- `echoscreencore:reference_dense_list`
- `echoscreencore:reference_settings`
- `echoscreencore:reference_inputs`
- `echoscreencore:reference_modal_overlay`
- `echoscreencore:reference_accessibility`

### `echoterminal`
- `echoterminal:terminal_overview`
- `echoterminal:terminal_mission_graph`
- `echoterminal:terminal_mission_browser`
- `echoterminal:terminal_addons`
- `echoterminal:terminal_recipe_index`
- `echoterminal:terminal_route_records`
- `echoterminal:terminal_discovery_grid`
- `echoterminal:terminal_faction_atlas`
- `echoterminal:terminal_archives`
- `echoterminal:terminal_vitals`
- `echoterminal:terminal_reward_inbox`
- `echoterminal:terminal_data_core`
- `echoterminal:terminal_settings`

### `echoindex`
- `echoindex:index_dashboard`
- `echoindex:index_items`
- `echoindex:index_recipes`
- `echoindex:index_usages`
- `echoindex:index_machines`
- `echoindex:index_mods`
- `echoindex:index_favorites`
- `echoindex:index_history`
- `echoindex:index_item_detail`
- `echoindex:index_recipe_detail`
- `echoindex:index_machine_detail`
- `echoindex:inventory_overlay`

### `echolens`
- `echolens:field_lens`
- `echolens:lens_overlay`

### `echohudcore`
- `echohudcore:native_hud`
- `echohudcore:mission_tracker`
- `echohudcore:hazard_readout`
- `echohudcore:compass_indicator`
- `echohudcore:screen_safe_area`

## Runtime Notes

- **NeoForge/Native:** Use the module page IDs directly through the module's own ScreenCore bridges.
- **Standalone Engine:** Maps canonical IDs to module page IDs via `AdapterCore` service publications, then renders through the Engine's ScreenCore runtime.
- **Standalone Runtime:** Uses legacy Java screens; parity target is to consume the same canonical IDs where feasible.
