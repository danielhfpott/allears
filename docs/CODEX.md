# All Ears — Codex Working Context

## Mission

Build All Ears as a practical Android accessibility application. The immediate objective is not to build the whole product. The immediate objective is to make the smallest real end-to-end interaction work.

## Current milestone: M0

Implement and validate:

**floating button → selection mode → select text → confirm → speak text aloud**

## Product constraints

- Never automatically speak incoming messages or other content.
- The user must explicitly initiate every reading action.
- Keep the visible interaction minimal.
- The app should be usable as an overlay while another app is open, subject to Android platform permissions and restrictions.
- Do not implement replay/settings/history yet unless required as scaffolding for M0.
- Do not add AI features.

## Engineering approach

1. Inspect the repository before making assumptions.
2. Choose the simplest Android architecture that can genuinely support the required interaction.
3. Validate platform feasibility early.
4. Implement the smallest vertical slice rather than building isolated infrastructure.
5. Test the actual interaction on a real Android device as soon as possible.
6. Record discoveries and platform constraints in `docs/ARCHITECTURE.md`.
7. Update milestone status after each meaningful validation.

## Speech provider

For early development, use a replaceable speech abstraction. A local/mock implementation may be used for UI and interaction testing if necessary, but the M0 acceptance path must ultimately demonstrate actual speech playback. ElevenLabs is the planned high-quality provider and can be integrated once the interaction path is proven.

Never hard-code API secrets into the repository.

## M0 acceptance test

A tester should be able to:

1. Launch/enable All Ears.
2. Open another Android app containing text.
3. Tap the All Ears floating button.
4. Select text.
5. Tap the confirmation control.
6. Hear the selected text spoken aloud.
7. Confirm that nothing spoke before explicit confirmation.

## What not to optimize yet

Do not spend the first milestone on branding, animations, settings, voice selection, replay, history, cloud infrastructure, analytics, or broad multi-platform support.

Reliability of the fundamental interaction is the priority.
