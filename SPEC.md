# SPEC — Arceus Run (2-Player Racing Game)

> Spec-Driven Development. This file is the source of truth. Code follows the spec.

## 1. Vision
A local 2-player tap-racing game. Each player picks an Arceus type-form, then taps
their half of the screen to make their Arceus sprint toward the finish line. Items
on the track boost or slow runners. First to the goal wins.

> IP note: All artwork is **original Arceus-inspired** vector/canvas art (white body,
> golden cross-wheel, type-colored ring). All audio is **original chiptune** generated
> with the Web Audio API. No official Pokémon assets or music are used.

## 2. Players & Input
- 2 players, same device, split screen (left = P1, right = P2).
- Control = **tap/click your half repeatedly** (button-mashing). Each tap adds an
  impulse to your Arceus' speed; speed naturally decays, so sustained tapping = sustained run.
- Keyboard fallback: P1 = `F`, P2 = `J`.

## 3. Core Loop
Title -> Character Select (both pick a type-form) -> Countdown (3-2-1-GO)
-> Race -> Win screen -> (Rematch / Change characters).

## 4. Mechanics
- Speed model: `speed += tapImpulse` on tap; every frame `speed *= friction`. Distance += speed.
- Track length: fixed goal distance with a progress track + camera.
- Items auto-collected on contact:
  - boost (+speed, green), slow (-speed, purple), shield (blocks next negative, blue),
    lightning (burst, yellow).
- Effects are timed and shown as icons above the runner.
- Win: first to reach goal distance. Winner + finish animation + confetti.

## 5. Type-Forms (roster)
18 forms keyed by type color: Normal, Fire, Water, Electric, Grass, Ice, Fighting,
Poison, Ground, Flying, Psychic, Bug, Rock, Ghost, Dragon, Dark, Steel, Fairy.
Each recolors the cross-wheel + eye-stripe accent.

## 6. Audio
- Background: looping original chiptune, toggleable mute.
- SFX: tap, item pickup, boost, slow, countdown beep, victory fanfare.
- Starts only after a user gesture (autoplay policy).

## 7. Improvements beyond the brief
- Shield + lightning items for depth. Mirrored item spawns per lane for fairness.
- Parallax background, running leg animation, dust particles, confetti.
- Mute button, keyboard fallback, responsive canvas, photo-finish, rematch flow.

## 8. Non-Goals
Online multiplayer, persistence, accounts, real Pokémon IP assets.

## 9. Acceptance Criteria
- [ ] Two players each select a distinct type-form.
- [ ] Tapping each half moves the matching Arceus; sprites animate.
- [ ] >= 4 item types affect speed/effects visibly.
- [ ] Clear winner declared at goal with audio + confetti.
- [ ] Original audio plays and can be muted. No console errors.
- [ ] One self-contained .html file; works on touch + keyboard.
