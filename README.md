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
- Fixes for all 14 minigames, with the logic and physics of each corrected for 60 and 120 FPS
- Works with the **[English fan translation](https://www.moddb.com/mods/ry-ga-gotoku-kenzan-english-translation-patch)**, including **patch 6**, and the **Japanese original**
- The game's 20 FPS cutscene sections run at the **full frame rate**, with their timing unchanged
- **Game speed stays correct when the frame rate drops**, as long as your PC keeps up
- **A sharper picture at any Resolution Scale:** the game no longer blurs its own finished frame
- Optional replacement shader that cleans up Depth of Field and corrects an edge filter at high resolution

## Supported versions

| Game version | Executable hash | Entries to enable |
|---|---|---|
| [English fan translation](https://www.moddb.com/mods/ry-ga-gotoku-kenzan-english-translation-patch) patch 6 (RPCS3 EBOOT) | `PPU-0f7ee1f50561dd854f48d4a74fbcb7b30f0307d6` | `... (English translation)` |
| English fan translation, initial release (RPCS3 EBOOT) | `PPU-5d3cde094c0be606290c4716da497bced59c1256` | `... (English translation)` |
| Japanese original | `PPU-fc24101547eff0f4307d4f70a0cb76329f11a525` | `... (Japanese original)` |

> [!NOTE]
> **English translation users:** make sure you followed the translation's *Extra Steps (RPCS3 Only)*: rename `EBOOT.BIN`
> to `EBOOT PS3.BIN`, then rename `EBOOT RPCS3.BIN` to `EBOOT.BIN`. The English entries also cover patch 6's real-PS3 EBOOT,
> `PPU-7bdd22e8...`, but that one has not been tested in RPCS3.

> [!NOTE]
> Game Patches shows the English `60 FPS` and `120 FPS` entries twice, once per hash, with the hash added to the name. Tick the
> one ending in your hash, or both: only the matching one applies.

Other English mods and other builds of the translation have a different hash, so the frame-rate entries will not apply to them.

Not sure which one you have? Boot the game once, close RPCS3, and search `log\RPCS3.log` for `PPU executable hash`. Use the
file rather than RPCS3's log window, which can hide that line.

<details>
<summary><b>Frame rate still 30?</b></summary>

The game's hash has to match one of the rows above. Game Patches lists every entry whether it matches or not, so ticking one
proves nothing. Check that:

1. `RPCS3.log` shows `PAT: Applied patch` with `60 FPS (...)` or `120 FPS (...)`. Only that line counts. Minigame lines appear
   only after a recompile or when you enter that minigame, so they say nothing about the frame rate.
2. The `PPU executable hash` line matches a row above, and you ticked that row's entries.
3. If the hash is not in the table, you have a different build. Please open an issue with that hash and where your English
   patch came from.

Clearing RPCS3's caches does not help with this.

</details>

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
| GPU → Framerate Limiter | **Auto** (Off lets the game run far too fast) |
| VSync | On only with a 120 Hz+ display, otherwise Off |

> [!IMPORTANT]
> Kenzan runs its logic once per frame, so in earlier versions a frame drop slowed the whole game down. Since 2.0 the game keeps
> its speed by drawing fewer frames when your PC falls behind, down to about 30 FPS. That helps as long as your PC keeps up with
> the game logic itself. If it cannot, the game slows down, and in cutscenes the picture falls behind the sound.
>
> **On a weaker PC, use the 60 FPS entry.** It asks much less of your CPU. Very crowded places, such as the Gion festival at
> night, are the hardest, and there the limit is the emulated graphics work, so a lower resolution scale may not help.

Menus, dialogue and the start of heat actions run at 60 FPS, exactly as in the original game. The sections of six cutscenes that
the original drops to 20 FPS run at the full frame rate of your entry. To switch back, set Vblank Rate to 60 and enable the 60 FPS
entry instead.

## Optional: cleaner Depth of Field and edges at high resolution

The game has an edge filter in its colour grade, set for 1280x720, so at a high Resolution Scale it reaches too far and softens
every edge. This file makes it reach one real pixel at any scale. The filter stays. At a high Resolution Scale, the game's Depth of Field blur also leaves a fine grid pattern on blurred backgrounds and crowds in
cutscenes. The blur takes its samples a fixed distance apart, and that spacing shows up as a mesh once the image is sharp enough.

`sh_iori_ps3.par` replaces the game's shader file with a copy in which those shaders are rewritten. Depth of Field stays on and
the grid goes away. It changes 50 of the file's 180 shaders and works with or without the frame-rate entries. It is tested on the
English translation: the edge filter at 100% and 300%, the Depth of Field blur at 300%.

1. Download [`sh_iori_ps3.par`](https://github.com/CptPakundo/YakuzaKenzanFPSPatch/releases/latest/download/sh_iori_ps3.par)
   from the [latest release](https://github.com/CptPakundo/YakuzaKenzanFPSPatch/releases/latest).
2. In your game folder, go to `PS3_GAME/USRDIR/bin/shader/` and make a backup of `sh_iori_ps3.par`.
3. Copy the downloaded file over it.

To undo it, restore your backup. Reinstalling the game puts the original back. This file is separate from the patch: nothing
in `imported_patch.yml` needs it.

## What gets corrected

<details>
<summary>Full list</summary>

- **Combat:** movement, strafing, turning, enemy AI (think rate, cooldowns, counter windows), heat gain and drain,
  knockdown and stun durations, grabs, mash prompts, sword slashes and afterimages, hit effects
- **Heat actions:** timeline speed, button and mash prompts, slow motion, weapon and limb trails, finishing effects
- **Cutscenes and events:** playback speed, slow-motion moments, chapter title cards, talk scenes (each plays once),
  talk cameras, skip timing, movie skip fade-out, subtitles, the 20 FPS sections
- **Field:** NPC behaviour and crowds, talk arrows above NPCs, dropped items, grass, trees, wind, sea water, splashes,
  rain splashes (on the ground and on characters in cutscenes), lights, particles, cloth, sound fades, doors and other
  animated scene parts
- **HUD and menus:** health and heat bars, text speed, result screens, map, pause-menu quit fade, restaurant meal and
  shop fades
- **Minigames:** Bowling, Chohan, Hanafuda, K Yabusame (Jiraiya training), Kamerace, Karuta, Konpira, Mahjong, R Yabusame, Shogi,
  Suika, Tintiro (Chinchirorin), Tousenkyo (including the fan's flight), Waterfall, plus scarecrow training and the minigames built
  into the main program.

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
- **Effects in the former 20 FPS cutscene sections** run at the same pace as the rest of the cutscene, which is 1.5x what the
  original did in those seconds.
- **VRR displays.** Since 2.0 the game no longer slows down when the frame rate moves around, so VRR works much better. Frame
  times still vary slightly, and some OLED panels show this as flicker, especially when the frame rate changes.
- **Short stutters are not fully absorbed.** A stall longer than about 50 ms still costs time. If something else on your PC is
  using all your CPU cores, you can see this as brief slow motion.
- Not every part of the game has been played with the patch yet. If something runs too fast or too slow compared with
  the original, please [open an issue](https://github.com/CptPakundo/YakuzaKenzanFPSPatch/issues).

When reporting, please include your game version, 60 or 120 FPS, what happened and where, and your `RPCS3.log` if the
game crashed. A patch that loaded shows up in the log as `PAT: Applied patch (... description='60 FPS (...)' ...)`.

## Credits

- **Whatcookie**, for the earlier Kenzan 60 FPS canary patch that found the engine's native frame-rate switch
- **FlexBy**, whose *Yakuza: Dead Souls* 60 FPS patch (same engine family) served as a reference
- **The [*Like a Dragon: Kenzan!* English Patch](https://www.moddb.com/mods/ry-ga-gotoku-kenzan-english-translation-patch) team** (majDima, Arcodeaus, jurxd, PauseForTheCat, TheEdgyNerd and helpers)
- **The [RPCS3](https://rpcs3.net) team**, for the emulator and its patch system, and
  **[AniLeo](https://github.com/AniLeo)** in particular, whose tidy-up of this patch on the game's RPCS3 wiki page was a
  gentle reminder that a real PS3 was never going to hit 120 FPS anyway
- **[Ghidra](https://github.com/NationalSecurityAgency/ghidra)** and **[GhidraMCP](https://github.com/bethington/ghidra-mcp)**,
  used for the analysis

Developed with AI assistance (Claude by Anthropic).

## License

[MIT](LICENSE). *Ryu ga Gotoku Kenzan!* is © SEGA. This project is not affiliated with SEGA or the RPCS3 team. The patch
contains no game files. The optional `sh_iori_ps3.par` is a modified copy of the game's shader file: it is not covered by the
MIT license, and you need your own copy of the game.

<!-- readme-reviewed: 2.0 -->
