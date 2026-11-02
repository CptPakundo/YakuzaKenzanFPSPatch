# Changelog

## 1.4 (2026-11-02)

- **No more crash in the chapter 2 opening cutscene at 120 FPS.** About four seconds into the rainy night cutscene that
  opens chapter 2, the game ran out of memory for particle effects and RPCS3 stopped with "The PS3 application has
  likely crashed". Rain splashes were created 4 times as often as in the original at 120 FPS (twice as often at 60 FPS),
  so far more of them were alive at once. Rain splashes on the ground and on characters now appear at the original rate
  at 60 and 120 FPS. As a safety net, if the effect memory ever fills up anyway, the game now skips that one particle
  instead of crashing. Thanks to BeanButCoffee for the report, the logs and the save file.
  ([#4](https://github.com/CptPakundo/YakuzaKenzanFPSPatch/issues/4))
- **No more sound stutter when skipping a movie.** Skipping an FMV (for example the intro movie) could make the movie's
  sound jump back up in short bursts while it faded out, heard as a stutter of about half a second. It happened on some
  skips only, mostly at 120 FPS. This was a timing race in the original game's movie player, which 120 FPS made easy to
  hit. The fade-out is now smooth. ([#4](https://github.com/CptPakundo/YakuzaKenzanFPSPatch/issues/4))

## 1.3 (2026-11-02)

- **No more freeze after eating at a restaurant.** After a meal (for example at Shirohebi Udon) the screen faded back in
  after the experience points, but the shop dialogue never returned and the game was stuck (at 120 FPS it stuck earlier,
  on the black screen). The meal's fades now run at the original speed and always finish. This affected every restaurant
  meal in releases 1.0 to 1.2, with both the 60 FPS and the 120 FPS entries.
  ([#3](https://github.com/CptPakundo/YakuzaKenzanFPSPatch/issues/3))

## 1.2 (2026-11-02)

- **Cutscene slow motion stays in sync.** The three cutscenes with slow-motion moments (chapters 7 and 10, and one
  substory) ended each slow-motion part slightly early, so the picture ran up to about 0.3 s ahead of the audio at
  120 FPS. They now end on the same frame as in the original.
- **Heat-action trails look right again.** Weapon and limb trails in heat actions were drawn too short and faded too fast
  at 60/120 FPS. They now match the original.
- **Quit fade back to normal.** Quitting to the title (or out of a minigame) from the pause menu faded to black over
  1-2 s instead of 0.5 s.
- **RPCS3 only.** Removed the entries for the English translation's real-PS3 EBOOT, matching the patch on the game's
  RPCS3 wiki page, where @AniLeo had already trimmed them (a fair reminder that no PS3 was going to run this at 120 FPS
  anyway). English translation users need the translation's RPCS3 EBOOT, see the README.

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
