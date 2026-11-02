# Changelog

## 1.1 (2026-11-02)

Fixes for the first two bug reports. Both apply to the 60 FPS and the 120 FPS entries.

- **Dialogue no longer plays twice.** Voiced talk scenes (for example arriving in Gion with the monk in chapter 4) could
  replay their dialogue a second time while the characters just stood there. The event that starts a talk now fires only
  once. ([#1](https://github.com/CptPakundo/YakuzaKenzanFPSPatch/issues/1), [#2](https://github.com/CptPakundo/YakuzaKenzanFPSPatch/issues/2))
- **Chapter title card no longer gets stuck.** At the start of a chapter, the title card could stay on screen during the
  whole opening cutscene while only its audio and subtitles played. The opening cutscene now waits for the fade to black
  to finish, so the title is cleared first. On fast PCs the black screen before chapter-opening cutscenes can last a
  little longer than in the original (up to about 2 s at 120 FPS).
  ([#1](https://github.com/CptPakundo/YakuzaKenzanFPSPatch/issues/1))

## 1.0 (2026-11-01)

First public release.

- 60 FPS and 120 FPS entries for the English fan translation (RPCS3 and PS3 EBOOT) and the Japanese original. Both are in
  one group, so only one can be active.
- Minigame fixes for 11 minigame modules, for both the translated and the original game files. Each entry serves both
  frame rates and does nothing when no frame-rate entry is enabled.
- About 300 corrected places in the main program: combat, enemy AI, heat, heat actions, cutscenes, cameras, HUD and
  menus, field effects, NPCs and the built-in minigames.
