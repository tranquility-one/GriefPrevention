# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

GriefPrevention is a Minecraft server plugin (Spigot/Paper) providing self-service anti-griefing land claim protection. Java 21, Maven build, GPL-3.0-or-later.

## Build Commands

```bash
mvn compile           # Compile
mvn verify            # Compile + run tests (preferred over `test` - includes integration checks)
mvn package           # Build plugin JAR (output: target/GriefPrevention.jar)
mvn test -Dtest=WordFinderTest  # Run a single test class
```

Tests use JUnit 5 + Mockito 5.16 with `-javaagent` and `reuseForks=false` (required due to Bukkit static state).

## Architecture

### Package Structure

Two package hierarchies coexist during an ongoing migration:

- **`me.ryanhamshire.GriefPrevention`** — Legacy core package containing the main plugin class and most gameplay logic (~90 files)
- **`com.griefprevention`** — Newer modular package with clearer separation:
  - `commands/` — Command handlers extending `CommandHandler` (base TabExecutor)
  - `protection/` — Interaction/protection logic (`InteractionProtectionHandler`, `ProtectionHelper`)
  - `visualization/` — Claim boundary rendering (fake blocks or particles)
  - `platform/` — Platform detection and platform-specific features (Spigot vs Paper)
  - `events/` — Custom Bukkit events (`ClaimCreatedEvent`, `TrustChangedEvent`, etc.)
  - `metrics/` — bStats integration
  - `util/` — Utilities (command monitoring, `IntVector`)

### Key Classes

- **`GriefPrevention`** (`me.ryanhamshire`) — Main plugin class (~3100 lines). Entry point, configuration, event handler registration, command setup. Hosts all config properties.
- **`Claim`** — Land claim with boundaries, permissions, parent-child subdivision support
- **`ClaimPermission`** — Permission hierarchy enum: `Edit > Manage > Build > Container > Access`
- **`DataStore`** (abstract) — Singleton managing all claim/player data with caching. Concrete impl: `FlatFileDataStore`
- **`PlayerData`** — Per-player state, claim blocks, statistics

### Event Handlers

- `BlockEventHandler` — Block break/place protection
- `PlayerEventHandler` — Player interactions, chat, command filtering
- `EntityEventHandler` / `EntityDamageHandler` — Entity damage, PvP rules
- `InteractionProtectionHandler` — Special interaction cases
- `KnockbackProtectionListener` — Platform-specific knockback protection

### Commands

Commands are defined in `plugin.yml` and registered to handler classes extending `CommandHandler`. Tab completion uses `TabCompletions.visiblePlayers`.

### Async Tasks

Scheduled `Runnable` implementations for deferred work: `WelcomeTask`, `FindUnusedClaimsTask`, `CleanupUnusedClaimTask`, `AutoExtendClaimTask`, `PlayerRescueTask`, etc.

## Code Style

- **Brace style**: Next-line (Allman) for classes, methods, blocks; end-of-line for lambdas
- **`else`/`catch`/`finally`**: On new line
- 4-space indent, 120 char max line length
- No wildcard imports (threshold set to 99999)
- Import order: `*`, blank, `javax.**`, `java.**`, blank, `$*`
- JetBrains `@NotNull`/`@Nullable` annotations for nullity
