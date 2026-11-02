# Yakuza Kenzan! 60/120 FPS Patch for RPCS3

![Emulator: RPCS3](https://img.shields.io/badge/emulator-RPCS3-blue)
![Game ID: BLJM60064](https://img.shields.io/badge/game%20ID-BLJM60064-lightgrey)
![FPS: 60 | 120](https://img.shields.io/badge/FPS-60%20%7C%20120-brightgreen)
![License: MIT](https://img.shields.io/badge/license-MIT-green)

RPCS3 patches that run *Ryu ga Gotoku Kenzan!* at **60 or 120 FPS**, with the game logic kept at its original speed.
Fights, heat actions, cutscenes, NPCs and minigames play as they did on the PS3, only smoother.

Normally, running Kenzan above 30 FPS speeds the whole game up. This patch uses the engine's own frame-rate setting and
then corrects the code that still counts frames: movement, AI, timers, effects, cameras, menus and the minigames.

## Features

- **60 FPS** with no extra emulator settings
- **120 FPS** for high-refresh displays (needs one setting, see below)
- Gameplay speed matches the original 30 FPS game, including enemy AI, heat gain, button prompts and cutscene timing
- Separate fixes for 11 minigames
- Works with the **English fan translation** and the **Japanese original**

## Supported versions

| Game version | Executable hash | Entries to enable |
|---|---|---|
| English fan translation (RPCS3 EBOOT) | `PPU-5d3cde094c0be606290c4716da497bced59c1256` | `... (English translation)` |
| Japanese original | `PPU-fc24101547eff0f4307d4f70a0cb76329f11a525` | `... (Japanese original)` |

> [!NOTE]
> **English translation users:** make sure you followed the translation's *Extra Steps (RPCS3 Only)*: rename `EBOOT.BIN`
> to `EBOOT PS3.BIN`, then rename `EBOOT RPCS3.BIN` to `EBOOT.BIN`. The patch only applies to the RPCS3 EBOOT, not to
> the real-PS3 one.

Not sure which one you have? Boot the game once, close RPCS3, and search `RPCS3.log` for `PPU executable hash`.

## Installation

1. Download [`imported_patch.yml`](https://github.com/CptPakundo/YakuzaKenzanFPSPatch/releases/latest/download/imported_patch.yml)
   from the [latest release](https://github.com/CptPakundo/YakuzaKenzanFPSPatch/releases/latest).
2. Place it in RPCS3's `patches` folder, keeping the name `imported_patch.yml`:

   | OS | Folder |
   |---|---|
   | Windows | `<RPCS3 folder>\patches\` |
   | Linux | `~/.config/rpcs3/patches/` |
   | macOS | `~/Library/Application Support/rpcs3/patches/` |

   Already have an `imported_patch.yml`? Merge the two files instead of replacing yours (see below).
3. In RPCS3, open **Manage → Game Patches** and find *Ryu ga Gotoku Kenzan!*. Enable:
   - **one** frame-rate entry for your version: `60 FPS (...)` **or** `120 FPS (...)`;
   - every `Minigame fixes - ...` entry for your version. They do nothing on their own, so they are safe to leave on.
4. Click **Save** and start the game. The first boot takes longer while RPCS3 recompiles the patched code.

<details>
<summary><b>Merging with an existing <code>imported_patch.yml</code></b></summary>

1. Keep a single `Version: 1.2` line at the very top of your file.
2. Copy everything below that line from this patch to the end of your file.
3. A file can only have one `Anchors:` section. If yours already has one, move this patch's indented anchor lines under
   your existing `Anchors:` line and delete the second `Anchors:` line.

</details>

## 60 FPS setup

Nothing to change. Keep RPCS3's defaults (**Vblank Rate 60**, **Framerate Limiter Auto**).

## 120 FPS setup

Right-click the game → **Create Custom Configuration**, then set:

| Setting | Value |
|---|---|
| Advanced → Vblank Rate | **120** (required, otherwise the game runs at half speed) |
| GPU → Framerate Limiter | Auto or Off |
| VSync | On only with a 120 Hz+ display, otherwise Off |

> [!IMPORTANT]
> Your PC has to hold a steady 120 FPS. Kenzan runs its logic once per frame, so frame drops slow the whole game down
> instead of skipping frames. Lowering the resolution scale helps the most.

Menus, dialogue and the start of heat actions run at 60 FPS and a few cutscenes at 20 or 30 FPS, exactly as in the
original game. To switch back, set Vblank Rate to 60 and enable the 60 FPS entry instead.

## What gets corrected

<details>
<summary>Full list</summary>

- **Combat:** movement, strafing, turning, enemy AI (think rate, cooldowns, counter windows), heat gain and drain,
  knockdown and stun durations, grabs, mash prompts, sword slashes and afterimages, hit effects
- **Heat actions:** timeline speed, button and mash prompts, slow motion, weapon and limb trails, finishing effects
- **Cutscenes and events:** playback speed, slow-motion moments, chapter title cards, talk scenes (each plays once),
  talk cameras, skip timing, subtitles
- **Field:** NPC behaviour and crowds, talk arrows above NPCs, dropped items, grass, trees, wind, sea water, splashes,
  lights, particles, cloth, sound fades
- **HUD and menus:** health and heat bars, text speed, result screens, map, pause-menu quit fade, restaurant meal and
  shop fades
- **Minigames:** Bowling, Chohan, K Yabusame, Kamerace, Konpira, Mahjong, R Yabusame, Shogi, Suika, Tousenkyo,
  Waterfall, plus scarecrow training and the minigames built into the main program. Hanafuda, Karuta and Chinchirorin
  already run at a fixed rate and need no patch.

</details>

## Known issues

- **Longer fades around loading.** Some fades to black at scene changes, for example before chapter-opening cutscenes,
  can last up to about 2 s at 120 FPS (1 s at 60) instead of about 0.5 s. Purely cosmetic.
- **Trails on regular attacks.** Some weapon and limb trails on normal attacks are shorter and fade faster than in the
  original (the same trails in heat actions are fixed).
- **Very slow storage.** If a cutscene voice line takes several seconds to load, it is skipped sooner than in the
  original.
- **Tiny timing differences.** Some timers can be off by less than 1/30 s after menus or dialogue; the walk animation
  while dragging a grabbed enemy and one branch of two story heat actions can run up to 1/40 s early; the scarecrow
  training dummies throw about 1-2% slower. A few fades and markers still update 30 times per second, as in the
  original, rather than being smoothed.
- Not every part of the game has been played with the patch yet. If something runs too fast or too slow compared with
  the original, please [open an issue](https://github.com/CptPakundo/YakuzaKenzanFPSPatch/issues).

When reporting, please include your game version, 60 or 120 FPS, what happened and where, and your `RPCS3.log` if the
game crashed. A patch that loaded shows up in the log as `PAT: Applied patch (... description='60 FPS (...)' ...)`.

## Credits

- **Whatcookie**, for the earlier Kenzan 60 FPS canary patch that found the engine's native frame-rate switch
- **FlexBy**, whose *Yakuza: Dead Souls* 60 FPS patch (same engine family) served as a reference
- **The *Like a Dragon: Kenzan!* English Patch team** (majDima, Arcodeaus, jurxd, PauseForTheCat, TheEdgyNerd and helpers)
- **The [RPCS3](https://rpcs3.net) team**, for the emulator and its patch system, and
  **[AniLeo](https://github.com/AniLeo)** in particular, whose tidy-up of this patch on the game's RPCS3 wiki page was a
  gentle reminder that a real PS3 was never going to hit 120 FPS anyway
- **[Ghidra](https://github.com/NationalSecurityAgency/ghidra)** and **[GhidraMCP](https://github.com/bethington/ghidra-mcp)**,
  used for the analysis

Developed with AI assistance (Claude by Anthropic).

## License

[MIT](LICENSE). *Ryu ga Gotoku Kenzan!* is © SEGA. This project is not affiliated with SEGA or the RPCS3 team and contains
no game files.
