# Changelog

## 2.0 (2026-11-06)

- **Game speed stays correct when the frame rate drops.** The game used to run its logic once per drawn frame, so any frame drop slowed
  everything down, a big reason why the Gion festival at night felt sluggish at 120 FPS. Logic now runs at a fixed rate on both entries,
  and when your PC falls behind, the game draws fewer frames instead, down to about 30 FPS. This works as long as your PC keeps up with
  the logic itself. On a PC that cannot, the game still slows down: use the 60 FPS entry. It does not raise the frame rate.
- **Fades around loading match the original.** A door, a battle, a mission-start talk and the fade before a chapter-opening cutscene were
  measured on no patch, 60 and 120: 0.5 s where the original has 0.5 s, not 2 s.
- **Two-button presses in a struggle get their original time.** Pressing both buttons together was twice as strict at 60 FPS and four times at 120.
- **Trails on regular attacks are back to their original length and fade.** Weapon and limb trails on normal attacks were a quarter as long
  at 120 FPS, half at 60, and faded 2 or 4 times too fast. They now gain a point 30 times a second, as in the original, so the tip can look
  slightly stepped. Measured in one short fight on each build: same point spacing, fade and scroll speed as with no patch.
- **All 14 minigames run at the full rate, with their logic and physics corrected.** New: Hanafuda, Karuta and Tintiro, and full rate for
  Mahjong, Shogi and Suika. They also keep their speed when frames drop, like the rest of the game. In Waterfall this keeps the notes on
  the music. A few motions step 60 times a second.
- **A sharper picture at any Resolution Scale.** The game's last pass offset the frame by half a pixel with filtering on, a 2x2 blur of
  every frame. The patch removes the offset. No effect is removed and no sharpening is added.
- **`sh_iori_ps3.par`:** the optional file now also corrects the edge filter in the game's colour grade, which was set for 1280x720 and
  reached three times too far at 300%. It now reaches one real pixel at any Resolution Scale.
- **The game's 20 FPS cutscene sections run at the full frame rate of your entry,** with the same cutscene timing. 1.7 held them at 60 FPS.
- **Fades run at their original length.** Some fades ran for 2 s instead of 0.5 s at 120 FPS, and the fade-in on entering free roam ran at
  30 FPS. Short fade-ins after talk missions are longer again, as in the original.
- **Menus and banners keep their speed when frames are skipped.**
- **Bowling keeps its timing.** At 60 FPS the throw ran at double speed and the ball left before Kiryu finished, and at 120 FPS the
  turn could end with the ball short of the pins. Wind-up, ball run and result now match the original on both entries, and the first
  page of View the Rules no longer goes missing at 120 FPS. The ball rolls at the full frame rate down the lane, and from just
  before the pins ball and pins step 30 times a second, as in the original. The same straight first ball dropped 8 pins on 36 of 43 throws in the original, 6 of 10 at 60 FPS and 2 of 12 at 120 FPS, where 6 of 12 were strikes against 2 of 43 in the original, so pin results are close at 60 FPS and looser at 120 FPS. Thanks to MrAdam36 for the report.
  ([#12](https://github.com/CptPakundo/YakuzaKenzanFPSPatch/issues/12))
- **Mahjong:** CPU turns take as long as in the original. They were about 12% short at 120 FPS.
- **Tousenkyo:** the menu after View the Rules no longer locks up at 60 FPS.
- **Tintiro:** the dice replay and the camera moves take as long as in the original. Both ran at double speed at 120 FPS.
- **K Yabusame:** the throw takes as long as in the original at 120 FPS.
- **Kamerace:** the turtles' bursts, the turning turtle in the info panel and the quit dialog's flash now run at the original rate.
- **Karuta:** the opening fades and the opponent's hand move at the original speed.
- **Suika:** player springs and timers no longer run at double rate at 120 FPS.
- **Fights:** just guard, sway lockout, standing health regeneration, heat stance, boss mode, gauge battles and grab limits keep the
  original timing.
- **Town and cutscenes:** rain drops, the time between NPC sounds in the street and colour grade blends take as long as in the
  original, and the short grace time after loading a save lasts as long as it should.
- **Talk menus flash for as long as in the original** in minigames that use them.
- **The letter scene after loading a save** moves at its original speed.
- **Fixed since 2.0rc1:** Shogi pieces no longer flicker, the Shogi toss spins at the original rate, and Karuta's camera shake no longer
  runs at double rate.
- **Upgrading from 1.7:** your ticks stay. Tick the three new entries, Hanafuda, Karuta and Tintiro.

- **Patches 6, 7, 8 and 9 of the [English fan translation](https://www.moddb.com/mods/ry-ga-gotoku-kenzan-english-translation-patch) work with the same entries.**
  Their EBOOTs and minigame modules are identical, so nothing needs changing.

## 1.7 (2026-11-05)

- **Support for patch 6 of the [English fan translation](https://www.moddb.com/mods/ry-ga-gotoku-kenzan-english-translation-patch).** Patch 6 has a new EBOOT, so the frame-rate entries did not
  apply to it and the game stayed at 30 FPS. The `(English translation)` entries now cover patch 6 as well as the initial
  release. RPCS3 lists them once per hash, so tick the line ending in your hash. The minigame entries needed no change,
  because patch 6 did not change the minigames. Thanks to Sheev_Approves66 for the report. ([#11](https://github.com/CptPakundo/YakuzaKenzanFPSPatch/issues/11))
- **The game's 20 FPS cutscene sections now run at 60 FPS.** Six cutscenes drop to 20 FPS for a while, about a minute of the whole
  game, and the longest is Morning After in chapter 8. They now run at 60 FPS on both the 60 and the 120 entry, with the same
  cutscene timing. Effects in those seconds run at the pace of the rest of the cutscene, a little faster than the original did
  there.
- **Doors open again.** The sliding door at Tatsuya did not open at 60 or 120 FPS. The original game stores a door's progress as
  a whole percentage, and at higher frame rates each frame adds too little to survive the rounding. The fix covers all such scene
  animations, including other doors such as the one at Tsuruya. The Tatsuya door was tested at 60 and 120 FPS; the others come from
  reading the game's files. Thanks to SK91no for the report and the videos.
  ([#10](https://github.com/CptPakundo/YakuzaKenzanFPSPatch/issues/10))
- **New optional file: `sh_iori_ps3.par`.** It removes the grid pattern that Depth of Field leaves on blurred backgrounds at high
  resolution. See the README for what it does and how to install it.
- **README:** added a "Frame rate still 30?" section and corrected the 120 FPS setup: Framerate Limiter must be Auto, not Off.

## 1.6 (2026-11-04)

- **Suika (Iaigiri Spirit Tempering) no longer crashes when it starts.** When RPCS3 compiled the minigames in the
  background, it could damage the first function of a minigame in its cache, which crashed Suika right after talking to the
  trainer. The patch now keeps that function intact in all 11 patched minigames. Thanks to RubrumRedEX and detect-henlo for
  the reports, logs and testing. ([#7](https://github.com/CptPakundo/YakuzaKenzanFPSPatch/issues/7))
- **The frame rate no longer drops to 30 after a Revelation in Spirit Tempering.** The original game forgets to undo one
  frame rate change at the end of that demo. That is invisible at 30 FPS, but with the patch the game stayed at 30 until
  a restart. This fix comes from reading the game's code, and MrAdam36 confirmed it in play. Thanks to MrAdam36 for the
  report. ([#9](https://github.com/CptPakundo/YakuzaKenzanFPSPatch/issues/9))

## 1.5 (2026-11-02)

- **Fan Toss: the fan flies as far as in the original.** In the Tousenkyo (fan toss) minigame at Azamiya, thrown fans
  lost their speed and dropped short at 60 FPS, and almost on the spot at 120 FPS, so they rarely reached the target.
  The minigame applies the fan's air resistance and lift once per physics step, which happened 2 or 4 times as often
  per second as in the original. They now act at the original rate, so a throw follows the same path as at 30 FPS.
  Thanks to Kyouma00001 for the report and the save file. ([#5](https://github.com/CptPakundo/YakuzaKenzanFPSPatch/issues/5))
- **No more crash in Jiraiya training.** Throwing a shuriken in the K Yabusame minigame crashed the game at 60 and
  120 FPS. At the higher frame rate the throw animation could trigger a second throw right after the first one, when
  there was no shuriken in hand any more. A throw now only happens with a shuriken in hand, as in the original.
  Thanks to detect-henlo for the report and the log. ([#6](https://github.com/CptPakundo/YakuzaKenzanFPSPatch/issues/6))

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
