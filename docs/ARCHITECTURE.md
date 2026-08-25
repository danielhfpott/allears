# All Ears — Architecture

## Architectural intent

Keep the user experience simple while allowing the underlying implementation to become sophisticated. Each major responsibility should have a clear boundary so that improvements do not require rewriting unrelated parts of the system.

## Initial pipeline

```text
User
  ↓
Floating overlay
  ↓
Selection mode
  ↓
Text capture
  ↓
Confirmation
  ↓
Speech engine
  ↓
Audio playback
```

## Core boundaries

### Overlay / interaction layer
Responsible for:
- showing the floating entry point;
- entering and leaving selection mode;
- presenting confirmation/cancel controls;
- providing clear state feedback.

### Text capture layer
Responsible for:
- obtaining the text explicitly selected by the user;
- normalizing selected content into a speech-ready text payload;
- dealing with Android platform/accessibility limitations.

### Speech layer
Responsible for:
- accepting text;
- requesting/generated speech audio from the selected provider;
- exposing loading/success/error state;
- returning playable audio to the playback layer.

The speech provider should be replaceable. ElevenLabs is a planned provider, but application logic must not be tightly coupled to an ElevenLabs-specific implementation.

### Playback layer
Responsible for:
- playing the generated audio;
- stopping playback when appropriate;
- reporting playback completion/failure.

Replay will later use the already-produced result rather than reimplementing the reading pipeline.

## Platform assumption

The initial target is Android because the required floating overlay and cross-application text-accessibility behavior need Android platform capabilities. The exact mechanism must be validated experimentally during M0 rather than assumed from documentation alone.

## Critical engineering principle

Do not confuse architectural separation with user-facing complexity. These boundaries are internal. The intended user interaction remains only:

1. Tap.
2. Select.
3. Confirm.
4. Listen.

## Unknowns to validate

- Exact Android APIs and permissions required for cross-app text selection/capture.
- Which classes of apps expose accessible text reliably.
- Whether selection can be performed directly over arbitrary apps or requires an accessibility-service-mediated interaction model.
- Overlay behavior across Android versions and OEM variations.
- Best speech playback path for low latency and reliable audio focus.
- Secure handling of future API credentials.
