# Track 1 — Challenge 01: Mobile transcript reader

This is my next pass on WhipScribe's mobile transcript reader.

## Product premise

On a phone, I think the core job is:

> Find the moment, understand who said it, and keep listening without losing your place.

I did not try to redesign the brand or add a new feature surface. The prototype changes the structure around the transcript so the content gets more of the viewport and controls appear only when their context makes them useful.

Open `index.html` in this directory. It includes current/proposed comparisons for each state I changed.

## What I changed

### 1. Preview CTA becomes part of the content boundary

The current reader has both a persistent player and a persistent "Keep reading" surface at the bottom.

I kept the player persistent and moved the conversion point into the transcript itself, exactly where the preview ends. This gives the transcript more usable height and avoids stacking two bottom surfaces.

### 2. Search stays one tap away

I did **not** put Search inside a generic "Actions" sheet.

Finding a phrase or moment is a primary transcript task, so Search remains directly available in the header. Entering search mode replaces the header with the search field and result navigation.

When the software keyboard is visible, the player collapses out of the way. Playback state is preserved.

### 3. The More menu becomes file-level actions only

The current More menu mixes navigation, account actions, reading settings, file management and feature entry points.

The proposed menu has four file-level actions:

- Export
- Rename
- Details
- Delete recording

Reading preferences belong with the reader. Account navigation belongs at the account/navigation level. Search remains directly exposed because it is a core task.

### 4. Text selection gets contextual actions

Selecting a transcript moment exposes only actions that make sense for the selection:

- Play from here
- Copy
- Ask about this

This keeps the selection state lightweight instead of opening another large menu.

### 5. Add an honest processing state

There is no processing state in the challenge today.

I deliberately avoid inventing an exact percentage or time estimate unless the backend can supply one reliably.

The screen says what is true:

- the recording is being transcribed
- the user can leave the page
- the transcript will appear here when ready
- audio can still be played when it is available

Skeleton transcript rows communicate where the result will appear without pretending partial text is final.

### 6. Multi-speaker layout for 320 px

Speaker names are placed in the transcript text column and shown once per turn.

This preserves the timestamp gutter and avoids creating another narrow speaker column. Four speakers remain distinguishable without shrinking the transcript body copy.

## What I deliberately kept

- **Timestamps in the gutter.** They connect transcript text to playback and make long transcripts easier to scan.
- **Persistent audio playback.** Reading and listening are one workflow here.
- **Transcript as a first-class tab.** AI features should not bury the source material.
- **Desktop layout.** This pass is intentionally mobile-only; none of these structural changes require a desktop redesign.

## Questions from the challenge

### What is the one thing a person on a phone came here to do?

Find a specific moment and understand it in context.

Search therefore stays one tap away rather than being nested under a generic actions menu.

### Keep reading bar + player: right trade?

I would keep only the player sticky.

The preview CTA appears at the content boundary, where the reason for the interruption is obvious. When the keyboard appears, the player temporarily collapses so it does not fight the keyboard for vertical space.

### Which More-menu items belong there?

Only file-level actions.

Search is direct. Reading settings belong with the reader. Account/navigation actions belong outside the recording overflow menu.

### Should Search, Download and Settings all feel like one panel?

They should share interaction quality, but they do not have equal importance.

Search is a primary task and stays directly exposed. Export and file actions can live in a sheet. Reading preferences are reader controls.

### What should processing look like?

A calm status screen that does not invent precision.

If the API cannot promise a percentage or ETA, the interface should not make one up.

### Four speakers at 320 px?

Speaker identity is attached to each turn inside the text column. The timestamp gutter stays unchanged.

### Text selection?

Selection creates a small contextual action bar: Play, Copy, Ask.

### Desktop?

Unchanged for this pass. That keeps scope tight and reduces regression risk.

## Scope

This prototype is intentionally static. It is meant to communicate hierarchy, state behavior and mobile interaction decisions, not pretend that production API behavior has already been implemented.
