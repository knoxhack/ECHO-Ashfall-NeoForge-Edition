# ECHO Ashfall NeoForge Edition

Minecraft/NeoForge Ashfall pack distribution. It consumes `-neoforge.jar` module artifacts.

## Purpose

Minecraft/NeoForge Ashfall pack distribution. It consumes `-neoforge.jar` module artifacts.

## What Lives Here

NeoForge edition manifests, release manifest templates, install/update docs, module requirement docs, rollback guidance, and troubleshooting notes.

## Release And Update Role

Owns Minecraft/NeoForge pack releases and pins `-neoforge.jar` module requirements resolved from `knoxhack/ECHO-Modules`.

## Public Or Private

Public is recommended when players or launchers need unauthenticated access to NeoForge pack metadata and release assets.

## Build And Dev Commands

Run commands from the repository root.

- `No build command is currently tracked in this repo.`

## Artifact Ownership

Pack manifests, pack archives, NeoForge install metadata, and per-file pack assets belong here. Shared module jars stay in `ECHO-Modules`.

## Release Assets

The current public alpha prerelease payload is tracked under `release-assets/v0.1.0-ashfall-neoforge-edition/`.

- `ashfall-neoforge-edition-0.1.0.zip` is stored with Git LFS.
- `ashfall-neoforge-edition-alpha-0.1.0.pack.json`, `echo-release.json`, and `checksums.txt` are checked in beside it.
- `release-audit.json` records the downloaded GitHub release asset hashes.

Current `v0.1.0-ashfall-neoforge-edition` assets are checksum-backed and declare 46 `moduleRequirements` for the `neoforge` artifact family. The rebuilt hotfix jars for Terminal, HoloMap, Lens, Index, ScreenCore, HUDCore, and Ashfall content entrypoints are published in `knoxhack/ECHO-Modules`, and the public Release Index now points at the matching pack, manifest, module, and channel artifact hashes. The Ashfall NeoForge lane has imported gameplay evidence for dev-direct launch, world load, HUD, Index, Terminal, HoloMap, Lens, creative tab search/selection/use, and save/reload. Computer Use screenshot capture is still blocked by the Windows capture API error `SetIsBorderRequired failed: No such interface supported (0x80004002)`, so the lane is backed by launcher-imported gameplay screenshots/logs rather than fresh Computer Use screenshots.

## Docs Index

- [docs/install.md](docs/install.md)
- [docs/update-flow.md](docs/update-flow.md)
- [docs/module-requirements.md](docs/module-requirements.md)
- [docs/rollback.md](docs/rollback.md)
- [docs/troubleshooting.md](docs/troubleshooting.md)

## Related Repos

- [knoxhack/ECHO-Launcher](https://github.com/knoxhack/ECHO-Launcher)
- [knoxhack/ECHO-Modules](https://github.com/knoxhack/ECHO-Modules)
- [knoxhack/ECHO-Ashfall-Native-Edition](https://github.com/knoxhack/ECHO-Ashfall-Native-Edition)
- [knoxhack/ECHO-Ashfall-Standalone-Edition](https://github.com/knoxhack/ECHO-Ashfall-Standalone-Edition)
- [knoxhack/ECHO-Release-Index](https://github.com/knoxhack/ECHO-Release-Index)
- [knoxhack/ECHO-Native-Platform](https://github.com/knoxhack/ECHO-Native-Platform)
- [knoxhack/ECHO-Standalone-Runtime](https://github.com/knoxhack/ECHO-Standalone-Runtime)
- [knoxhack/ECHO-SDK](https://github.com/knoxhack/ECHO-SDK)
- [knoxhack/ECHO-Developer-Studio](https://github.com/knoxhack/ECHO-Developer-Studio)
- [knoxhack/ECHO-Addons-Studio](https://github.com/knoxhack/ECHO-Addons-Studio)
- [knoxhack/ECHO-Platform-Website](https://github.com/knoxhack/ECHO-Platform-Website)
