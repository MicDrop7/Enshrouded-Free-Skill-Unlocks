# Free Skill Unlocks

**Version 1.1.0** · Enshrouded Mod Loader (Lua) · Download: [free-skill-unlocks-1.1.0.zip](free-skill-unlocks-1.1.0.zip)
(or from [Releases](https://github.com/MicDrop7/Enshrouded-Free-Skill-Unlocks/releases/tag/v1.1.0)) ·
Older: [1.0.0](free-skill-unlocks-1.0.0.zip)

## What it does

Every skill tree node costs **0 skill points** (configurable in `config.txt`), so a character can unlock as many
skills as they like. Optional: keep normal costs and/or change the skill points per level.

It changes nothing else: no recipes, world presets, perk, durability or dismantle values. Skill prerequisites stay as
normal: the game's unlock check cannot be changed by a data mod.

### Who decides

Skills are checked by whoever runs the world: your own game in solo or when you host, or the server on a dedicated
server. The mod only works in worlds that run it. If you join a world whose host or server does not have it, that host
resets the skills you did not pay for. Your game may still show 0 costs there, but the unlocks will not stick.

## Requirements

**Enshrouded Mod Loader (EML)**: `dbghelp.dll` from <https://github.com/brabb3l/kfc-parser/releases>

Copy it next to `enshrouded.exe` (or the server's `.exe`). It runs by itself when the game or server starts.

## Installation

> **Before first use, back up your character save.**

### Solo, or hosting a co-op world

1. Extract the zip into the game's `mods` folder, so you have:
   ```
   ...\steamapps\common\Enshrouded\mods\free-skill-unlocks\mod.json
   ```
   (not `mods\free-skill-unlocks\free-skill-unlocks\`)
2. Start the game.

Friends who join your world should install the mod too, with the same `config.txt`.

### Dedicated server

1. Stop the server.
2. Extract the zip into the server's `mods` folder, so you have:
   ```
   <server root>\mods\free-skill-unlocks\mod.json
   ```
3. Start the server. EML patches the game data on startup.
4. Each player who should get free skills installs the mod in their own game, with the same `config.txt`.

Players without the mod see normal costs. This is not tamper-proof: anyone with a copy of the mod folder can use it.

## Settings (`config.txt`)

| Setting | Meaning |
|---|---|
| `enabled` | `true` / `false` |
| `skillNodeCost` | cost per node level; `0` = free, `-1` = keep normal costs (only ever lowers costs) |
| `skillPointsPerLevel` | `0` = unchanged; any other number replaces the points per level |
| `patchDevSkillTree` | also patch the developer tree if present |
| `logNodes` | log every patched node (troubleshooting) |

Normal costs but more points per level:

```
skillNodeCost=-1
skillPointsPerLevel=5
```

## Check it worked

Open the newest file in the `logs` folder next to the game or server `.exe` and look for:

```
[Free Skill Unlocks] v1.1.0 on client: trees=1 | nodes=... costLoweredTo0=...
```

("on server" on a dedicated server.) `trees=0`, or `failed=` above 0, means a game update changed the data and the
mod needs updating.

## Uninstalling

Without the mod the game uses normal costs and points again, and resets skills that were not paid for. Reset your
skills in game while the mod is still installed, then delete the `free-skill-unlocks` folder.

## Credits

- Enshrouded Mod Loader (EML) / kfc-parser by brabb3l: required, not included.
- Auto Loot Plus by Dellemann: the settings reader and helper functions follow its code patterns. MIT License (the
  licence names the author as "cw"); the licence text is in `licences\MIT LICENSE.txt` in the zip.

---

More Enshrouded mods by MicDrop7: [Enshrouded-Game-Mods](https://github.com/MicDrop7/Enshrouded-Game-Mods).
