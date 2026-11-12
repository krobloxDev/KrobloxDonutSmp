# KrobloxDonutSMP

A DonutSMP-style survival plugin for Paper and Folia servers. It bundles the economy, PvP modes, player tools, staff tools and GUI menus that a survival network normally needs into a single jar.

![Java](https://img.shields.io/badge/Java-21-orange)
![Minecraft](https://img.shields.io/badge/Minecraft-1.21%2B-brightgreen)
![Platform](https://img.shields.io/badge/Platform-Paper%20%7C%20Folia-blue)

---

## Features

- **Economy**: money and shards, `/pay`, `/shardpay`, leaderboards, sell menus with multipliers, a worth browser and sell history.
- **Marketplace**: auction house, orders board, shard shop, crates with keys and key-all events, and a Billford trade menu.
- **PvP**: ranked PvP arena, 1v1 duels with a queue and draws, instanced FFA arenas, bounties and a combat manager.
- **Teleportation**: homes, warps, spawn, an AFK zone, random teleport with a matchmaking queue, RTP portals and TPA with auto-accept.
- **Social**: teams, friends, private messages, an ignore list and global chat settings.
- **Staff tools**: staff mode with vanish, freeze, invsee, alt detection, staff chat, reports and helpop, a full punishment suite with history, and command and chat logs.
- **Server tools**: spawners, cuboid regions, amethyst tools, lag clearing, maintenance mode, player wipe and restore, and server wipe.
- **GUI first**: menus, a settings screen, a scoreboard, a tablist and a pause-screen menu are all configurable.
- **Languages**: English, German, Spanish, French, Indonesian, Portuguese (Brazil), Russian and Chinese (Simplified).
- **PlaceholderAPI**: built-in expansions for economy, leaderboards, ranks and disguise state.

---

## Requirements

| Requirement | Details |
|---|---|
| Server | Paper or Folia, Minecraft 1.21+ |
| Java | 21 |
| Required plugins | [ProtocolLib](https://github.com/dmulloy2/ProtocolLib), [PlaceholderAPI](https://github.com/PlaceholderAPI/PlaceholderAPI) |
| Optional plugins | LuckPerms, Vault, Apollo, Multiverse-Core, Floodgate, Simple Voice Chat |

The pause-screen menu needs Paper 1.21.6 or newer on both server and client.

---

## Installation

1. Stop the server.
2. Put `KrobloxDonutSMP.jar` in your `plugins/` folder, together with ProtocolLib and PlaceholderAPI.
3. Start the server. The plugin creates `plugins/KrobloxDonutSMP/` with all its configuration files.
4. Edit the files to your liking, then run `/kds reload`.
5. If you use the pause-screen menu, restart once more so the generated datapack is loaded, then rejoin.

---

## Commands

The main admin command is `/krobloxdonutsmp`, with the aliases `/kds` and `/kdsmp`. Every command can be switched off in the configuration.

| Area | Commands |
|---|---|
| Economy | `/balance` (`/bal`, `/money`), `/pay`, `/shards`, `/shardpay`, `/sell`, `/sellhand`, `/sellall`, `/sellmulti`, `/sellprogress`, `/sellhistory`, `/worth`, `/meta`, `/shardshop` |
| Marketplace | `/shop`, `/orders`, `/auctionhouse` (`/ah`), `/crates`, `/keys`, `/billford`, `/spawner` |
| PvP | `/duel`, `/queue`, `/leave`, `/draw`, `/ffa`, `/ffastats`, `/pvp`, `/bounty`, `/leaderboard` (`/lb`, `/top`, `/baltop`) |
| Teleportation | `/home`, `/homes`, `/sethome`, `/delhome`, `/renamehome`, `/spawn`, `/warp`, `/rtp`, `/rtpq`, `/afk`, `/tpa`, `/tpahere`, `/tpaccept`, `/tpadeny`, `/tpacancel`, `/tpauto` |
| Social | `/team`, `/friend`, `/friends`, `/msg`, `/reply`, `/pm`, `/ignore`, `/unignore`, `/chat` |
| Info and player | `/stats`, `/playtime`, `/ping`, `/settings`, `/ranks`, `/rules`, `/help`, `/servers`, `/discord`, `/store`, `/social`, `/nightvision`, `/enderchest` (`/ec`) |
| Staff | `/staffmode`, `/stafflist`, `/staffchat`, `/vanish`, `/freeze`, `/invsee`, `/ecsee`, `/alts`, `/fly`, `/flyspeed`, `/heal`, `/feed`, `/gamemode`, `/god`, `/teleport`, `/report`, `/helpop`, `/profileviewer`, `/seehomes`, `/logs`, `/chatlog` |
| Punishments | `/ban`, `/tempban`, `/mute`, `/tempmute`, `/vcmute`, `/warn`, `/kick`, `/blacklist`, `/unban`, `/unmute`, `/offend`, `/punishments` |
| Admin | `/kds`, `/addmoney`, `/removemoney`, `/setmoney`, `/addshards`, `/removeshards`, `/setshards`, `/setspawn`, `/setwarp`, `/delwarp`, `/warpmanager`, `/portalmanager`, `/cuboid`, `/arena`, `/ffaarena`, `/crate`, `/clearlag`, `/maintenance`, `/playerwipe`, `/playerunwipe`, `/serverwipe` |

---

## Permissions

Permissions are grouped under one prefix, `krobloxdonutsmp.`:

| Node | Purpose | Default |
|---|---|---|
| `krobloxdonutsmp.admin` | Parent admin node: reload, setup, wipes and the other `admin.*` tools | op |
| `krobloxdonutsmp.admin.<feature>` | Admin access to one feature, for example `admin.shop` or `admin.crate.reload` | op |
| `krobloxdonutsmp.command.<command>` | Use one command, following the pattern `krobloxdonutsmp.command.home` | per command |
| `krobloxdonutsmp.staff.<feature>` | Staff tools such as freeze, invsee, punishments and staff chat | op |
| `krobloxdonutsmp.updatechecker` | Receive the update notice on join | op |

The auction house also has its own `donutauction.*` nodes (`use`, `buy`, `sell`, `my`, `claims`, `cancel`, `limit`).

Granting `krobloxdonutsmp.admin` to a LuckPerms group is the quickest way to set up your admins:

```
/lp group admin permission set krobloxdonutsmp.admin true
```

---

## Placeholders

KrobloxDonutSMP registers several PlaceholderAPI expansions. Use them in your scoreboard, tablist, chat format or any other plugin that supports PlaceholderAPI.

| Expansion | Example |
|---|---|
| `%economy_*%` (also `%kds_*%` and `%krobloxdonutsmp_*%`) | `%economy_money%`, `%economy_money_formatted%`, `%economy_money_short%`, `%economy_shards%`, `%economy_kills%` |
| `%economylb_*%` | `%economylb_<type>_<position>_<property>%` for leaderboard entries |
| `%economyrank_*%` | `%economyrank_<type>%` for a player's leaderboard position |
| `%hide_*%` | `%hide_active%`, `%hide_name%` for disguise state |

---

## Configuration

All files live in `plugins/KrobloxDonutSMP/`:

| File | Controls |
|---|---|
| `config.yml` | General settings, chat, teleports, tablist, optimization and feature toggles |
| `messages.yml` and `languages/` | Every message, per language |
| `menus.yml` | Shared GUI layouts |
| `shop.yml`, `worth.yml`, `orders.yml`, `auction-house.yml` | Economy and marketplace |
| `crates.yml`, `spawners.yml`, `amethyst-tools.yml` | Crates, spawners and tools |
| `duels.yml`, `ffa.yml`, `pvp.yml` | Combat modes |
| `rtp.yml` | Random teleport and portals |
| `staff-mode.yml`, `freeze.yml`, `invsee.yml`, `offenses.yml`, `filter.yml` | Staff and moderation |
| `scoreboard.yml`, `dialog.yml` | Scoreboard and pause-screen menu |
| `database.yml` | Storage backend |

Missing files and keys are added automatically on startup. Use `/kds reload` to apply changes without a restart.

---

## Support

Found a bug or have a suggestion? Open an issue on the [issue tracker](../../issues). When you report a problem, include:

- the plugin version and jar file name
- your server software and version
- your Java version
- the relevant part of the console log and your config
