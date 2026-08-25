# All Ears

All Ears is an accessibility-first mobile app designed to let a person who is word-blind or otherwise has difficulty reading text **choose when text is read aloud**.

## Core principle

The app must never unexpectedly speak. The user initiates every reading action.

## MVP interaction

1. A small floating All Ears button is available as an overlay.
2. The user taps the floating button.
3. The app enters selection mode.
4. The user taps/selects one or more pieces of visible text.
5. The user confirms with a simple, familiar confirmation control (initially a check mark).
6. The selected text is converted to speech and played aloud.

That is the first functional target. Nothing else should block getting this pipeline working.

## Important constraints

- No automatic reading.
- No unsolicited audio.
- The floating control should be accessible without requiring the user to navigate away from the current app.
- The app should remain usable after the phone's normal close/back/home interactions where the operating system permits an overlay/accessibility service to remain active.
- The implementation must prioritize reliable text capture and speech playback over cosmetic features.
- ElevenLabs is a planned speech provider, but the speech provider should remain replaceable behind a clean internal interface.
- Replay, voice settings, speed settings, history, personalization, and polish are later layers and must not complicate the MVP.

## Product philosophy

All Ears is intended to be a genuinely useful assistive tool, not merely a technical demo. The architecture should therefore support substantial future functionality while keeping each development milestone independently understandable and testable.

## Context architecture

This repository is the evolving source of truth for the product. It should preserve:

- the user's needs and intended experience;
- product requirements;
- architectural decisions and their rationale;
- known platform limitations;
- implementation milestones;
- discoveries from testing;
- decisions that should not be silently reversed;
- the current state needed by an AI coding agent such as Codex.

The goal is to let implementation agents build from structured context rather than relying on a giant one-off prompt.

## Milestones

### M0 — Working speech pipeline

**Goal:** prove the core interaction end-to-end.

Floating overlay → selection mode → text selection → confirmation → speech playback.

### M1 — Reliable cross-app text capture

Improve coverage and reliability across realistic Android apps and text surfaces, using the appropriate Android accessibility/overlay mechanisms.

### M2 — Replay

After a successful reading, provide a simple replay action for the most recently spoken selection. This is a separate layer from the speech pipeline itself.

### M3 — Speech quality

Integrate ElevenLabs or another suitable provider, voice selection, speed controls, and robust handling of network/API failures.

### M4 — Accessibility and interaction polish

Refine touch targets, visual feedback, selection UX, cancellation, loading states, error states, and accessibility semantics.

### M5 — Broader product

Only after the core experience is reliable: history, personalization, additional reading modes, richer settings, and other features justified by actual use.

## Current implementation rule

**Do not build M1–M5 before M0 works.**

Every milestone should leave the repository in a coherent, runnable state and update this source of truth with what was actually learned.
