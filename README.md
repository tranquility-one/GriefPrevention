# GriefPrevention

<p align="center">
<img alt="GriefPrevention" width=100% height=auto src="https://repository-images.githubusercontent.com/68339667/9b3f7c00-ce61-11ea-82d1-208eaa0606e8">
</p>

[![GitHub release](https://img.shields.io/github/v/release/GriefPrevention/GriefPrevention)](https://github.com/GriefPrevention/GriefPrevention/releases/)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![standard-readme compliant](https://img.shields.io/badge/readme%20style-standard-brightgreen.svg)](https://github.com/RichardLitt/standard-readme)

Self-service anti-griefing land claim plugin for Minecraft servers since 2011.

Stop _responding_ to grief and prevent it instead. GriefPrevention stops grief before it starts automatically without any effort from administrators, and with very little (self-service) effort from players. Players create and manage their own land claims using in-game tools — no admin intervention required.

[Watch this video](https://www.youtube.com/watch?v=hKrA6NXn7Sc) to see how GriefPrevention works in-game.

## Table of Contents

- [Background](#background)
- [Install](#install)
- [Usage](#usage)
- [Addons](#addons)
- [Versions](#versions)
- [Contributing](#contributing)
- [Support](#support)
- [License](#license)

## Background

GriefPrevention was created in 2011 to provide a grief prevention solution that requires no administrator effort. It uses a claim-based land protection system where players can create, resize, and manage their own claims using a golden shovel.

### Supported Platforms

GriefPrevention targets and supports the latest available versions of **Spigot**, **Paper**, and **Purpur**. Other server implementations of the Bukkit API _should_ work but are untested. Older versions can be found on [BukkitDev](https://dev.bukkit.org/projects/grief-prevention/files) but are not supported.

## Install

1. Download the latest `GriefPrevention.jar` from [GitHub Releases](https://github.com/GriefPrevention/GriefPrevention/releases/).
2. Place the JAR in your server's `plugins/` directory.
3. Restart your server.

### Building from Source

Requires Java 21 and Maven.

```sh
mvn package
```

The built plugin JAR will be at `target/GriefPrevention.jar`.

## Usage

Once installed, GriefPrevention works out of the box with no configuration required. Players can create land claims using a golden shovel and manage trust permissions with commands.

See the [documentation](https://r.griefprevention.com/docs) for full configuration and usage details.

## Addons

[Addons](https://r.griefprevention.com/addons) provide additional features to GriefPrevention. Available addons are listed in [GitHub Discussions](https://r.griefprevention.com/addons).

## Versions

### GriefPrevention Legacy (v16)

GriefPrevention Legacy is version 16, currently recommended for production servers. It continues to receive official updates. Development happens on the `legacy/v16` branch — target this branch for Legacy pull requests.

### Version 17 and above

Newer major versions are developed on the `master` branch. These versions contain **breaking changes** and should **not** be used on production servers.

## Contributing

Contributions are welcome. Please open an [issue](https://github.com/GriefPrevention/GriefPrevention/issues) or submit a pull request. For Legacy changes, target the `legacy/v16` branch; for current development, target `master`.

## Support

- [Documentation](https://r.griefprevention.com/docs) — Learn how GriefPrevention works. Contains answers to most questions.
- [Issue Tracker](https://github.com/GriefPrevention/GriefPrevention/issues) — Report bugs. Check for existing reports before posting.
- [GitHub Discussions](https://github.com/GriefPrevention/GriefPrevention/discussions) — Feature requests and general discussion.
- [IRC Chat](https://griefprevention.com/chat/) or [Discord](https://r.griefprevention.com/dumcord/)

## License

[GPL-3.0-or-later](LICENSE.txt)

[![bStats](https://bstats.org/signatures/bukkit/GriefPrevention-legacy.svg)](https://bstats.org/plugin/bukkit/GriefPrevention-legacy)
