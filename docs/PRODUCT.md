# All Ears — Product Requirements

## User problem

Some people can understand spoken language well but have significant difficulty reading written words. All Ears gives them an intentional, low-friction way to have selected text spoken aloud wherever they encounter it on their phone.

## Primary user experience

The user is already looking at something on their phone. They should not have to copy text into another application, open a separate reader, or wait for automatic detection.

They tap the All Ears floating control, select what they want read, confirm, and hear it.

## Interaction contract

**Idle**
- Small floating control is available.
- It does not speak or interrupt.

**Selection mode**
- Activated explicitly by the user.
- The user can select multiple text items where technically supported.
- There is a clear way to cancel.
- The interface makes it obvious what is currently selected.

**Confirmation**
- A familiar check-mark style control is preferred for the first version.
- Confirmation starts the reading pipeline.

**Speaking**
- Selected text is sent to the speech layer.
- Audio is played to the user.
- Errors must fail visibly and quietly; never produce unexpected speech.

## Non-goals for MVP

- Automatic reading of incoming messages.
- Background monitoring of notifications for the purpose of speaking them automatically.
- Full settings system.
- Voice marketplace.
- Reading history.
- Cloud synchronization.
- AI rewriting or summarization.
- Translation.

## Design principle

Functionality and design are tightly coupled here. The UI should express the interaction state directly rather than add decorative complexity.

The first interface should therefore be extremely small:

**floating button → selection → confirmation → spoken result**

## Success criterion for M0

A real user can open another Android app containing readable text, invoke All Ears, select text, confirm, and hear that exact text spoken aloud reliably.
