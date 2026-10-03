# STRSC BlissGems

A customized build of the **BlissGems** plugin (a Bliss SMP style gem system) for Paper, Purpur and Folia servers running Minecraft 1.21+.

Players equip a gem in their **offhand** for passive effects and use it in their **main hand** to trigger powerful abilities. Gems have energy, can be upgraded, and can be lost to other players in combat.

> Based on BlissGems by **magicc / XoperrDev** ([xoperr.dev](https://xoperr.dev)). This is a modified build, not the official release. See [License](#license).

---

## Features

- **8 gems:** Astra, Fire, Flux, Life, Puff, Speed, Strength, Wealth
- **Two upgrade tiers** per gem, upgraded with the Gem Upgrader
- **Energy system:** gain energy on kills, lose it on death. Low energy weakens a gem, and zero energy breaks it
- **Single gem only:** one active gem per player (configurable)
- **Random starter gem** for new players, with an exclude list (Auratus, Heretic and Gold are excluded by default)
- **Gem Trader** (this build's Trader Patch)
- **Gold Gem event:** a one-time gem crafted from Wire Fragments and a Fragment Core, with a harvest ceremony when a holder is killed
- **Repair kits and pedestals** to restore gem energy
- **Revive beacons** to bring players back
- **Restoration Book** ritual
- **Energy bottles**, **Prismatic Edge** legendary sword, **enchant limiter**, **spawn beacon**, **broken mythic respawn** and **End sky** atmosphere
- **Auto-enchant** for tier 2 gems (tier 1 optional)
- **WorldGuard support:** disable gem abilities in chosen regions (for example `spawn`)
- Fixed-hearts tools: `/fixhearts` and `/fixedhearts`
- Gem news board with `/news`
- Gems are soulbound by default and cannot be dropped, stored in containers, or hopper-moved

## Requirements

- Java 21
- Paper, Purpur or Folia, Minecraft 1.21+
- Optional: WorldGuard, ProtocolLib

## Installation

1. Stop your server.
2. Drop the jar into `plugins/`.
3. Start the server once to generate `plugins/BlissGems/config.yml` and `recipes.yml`.
4. Edit the config if you like, then restart or reload.
5. Run **`/bliss smp start`** to start the SMP. This gives a gem to every online player who doesn't have one.

## Starting the SMP

New players only receive their first gem **after the SMP has started**. Until then they see a message saying gems are given when an admin runs `/bliss smp start`.

- Start it with `/bliss smp start`, or set `smp.started: true` in `config.yml`.
- `smp.auto-start-threshold` can auto-start the SMP once enough players have received gems.
- If you replace the jar and the config regenerates, `smp.started` returns to `false`. Run the start command again.

## Commands

| Command | Description | Permission |
|---|---|---|
| `/bliss` (aliases `/gems`, `/bg`) | Main command: info, pockets, trust, ability bindings, click toggle and more | `blissgems.user` |
| `/bliss smp start` | Start the SMP and hand out gems | `blissgems.admin` |
| `/bliss give <player> <gem>` | Give a gem (admin) | `blissgems.admin` |
| `/fixhearts [player]` | Reset max health to vanilla | `blissgems.fixhearts` |
| `/fixedhearts everyone <true\|false>` | Force 10 hearts on join | `blissgems.fixedhearts` |
| `/news` (alias `/gemnews`) | View the gem news board and repair windows | `blissgems.user` |

## Permissions

| Permission | Default | Description |
|---|---|---|
| `blissgems.*` | op | All permissions |
| `blissgems.admin` | op | Admin commands (give, energy, reload, smp start) |
| `blissgems.user` | everyone | Player commands and gem use |
| `blissgems.fixhearts` | op | Use `/fixhearts` |
| `blissgems.fixedhearts` | op | Use `/fixedhearts` |

## Configuration

Everything lives in `plugins/BlissGems/config.yml` and `recipes.yml`. The main sections are:

- `gems`: enable or disable gems, single-gem rule, starter pool exclusions, droppable gems
- `smp`: start flag and auto-start threshold
- `energy`: starting energy, kill/death gains and losses, thresholds
- `worldguard`: blacklist or whitelist regions for abilities
- `gold`, `upgrader`, `trader`, `repair-kit`, `revive-beacon`, `restoration`: feature settings
- `messages`: every player-facing message, with color codes

## Troubleshooting

**New players don't get a gem**
- Check `smp.started` in `config.yml`. If it is `false`, run `/bliss smp start`.
- Make sure at least one gem is enabled under `gems.enabled`, otherwise the random pool is empty.
- Players with `received-first-gem: true` in `plugins/BlissGems/playerdata/` won't get another one. Give it manually with `/bliss give <player> <gem>`.
- Check the console for BlissGems errors when the player joins.

## Credits

- **BlissGems** by magicc / XoperrDev, the original plugin
- **STRSC (Starscourge):** modifications and Trader Patch

## License

The original BlissGems plugin belongs to its author and is under its own license. STRSC's own changes are covered by the terms in [`LICENSE`](LICENSE), which does not grant any rights to the original plugin.
