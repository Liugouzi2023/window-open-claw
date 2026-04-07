# Exchange Lifecycle

## Purpose

Define how structured handoff files in `$OPENCLAW_SHARED_ROOT/exchange` should be understood and managed.

This file exists to prevent ambiguity between:

- latest vs historical files
- active vs stale files
- real handoffs vs examples
- consumed outputs vs still-relevant outputs

---

## Core Rule

The exchange directory is a structured handoff surface, not a dumping ground.

Files in exchange should remain understandable without reading chat history.

---

## Allowed Handoff Meaning

### `approved_brand`

Meaning:

- approved trademark brand contract
- originated by `trademark`
- usable downstream by `main` and `logo`

### `logo_request`

Meaning:

- explicit visual request
- may be originated by `main` from user intent
- may reference an `approved_brand` when available

### `logo_brief`

Meaning:

- structured visual brief
- originated by `logo` from a valid `logo_request`

Examples and templates must not be confused with live handoffs.

---

## Naming Rule

A handoff filename should make these visible when possible:

1. handoff type
2. subject or brand name
3. timestamp

Examples:

- `approved_brand_<brand>_<timestamp>.json`
- `logo_request_<brand>_<timestamp>.json`
- `logo_brief_<brand>_<timestamp>.json`

This makes historical ordering visible even before opening the file.

---

## Active Reading Rule

When reading exchange files for live work:

- prefer the newest valid file of the needed type
- do not assume the oldest or first-listed file is active
- do not use example/template files as live inputs
- if multiple candidate files exist, compare timestamps and purpose before acting

---

## Example Isolation Rule

Examples, templates, and reference artifacts should remain visibly separate from live handoffs.

Preferred approach:

- keep examples under `exchange/examples/`
- do not treat `*.example.*` or files under `examples/` as live work items

---

## Historical Retention Rule

Historical handoff files may remain for audit and traceability.
But historical retention must not make the current active state ambiguous.

That means:

- current work should be identifiable by timestamp and type
- historical files should not be mistaken for active instructions
- old files may remain, but should be interpreted as history unless they are the newest valid handoff for the same subject and type

---

## Consumption Rule

A handoff file is not automatically invalid just because it has been read.
It remains valid until superseded by a newer valid handoff of the same functional role.

In practice:

- a newer `approved_brand` supersedes an older one for the same brand context
- a newer `logo_request` supersedes an older one when it clearly replaces the visual request
- a newer `logo_brief` supersedes an older one when it is the updated downstream brief

Do not invent hidden consumed-state semantics unless the system later adds them explicitly.

---

## Reading Priority Rule

When multiple files exist, decide in this order:

1. correct handoff type
2. correct subject/brand
3. newest timestamp
4. valid origin role
5. whether it is clearly live rather than example/reference material

---

## Cross-Profile Rule

Exchange files are the only approved cross-profile handoff mechanism in this rebuilt system.

Therefore:

- do not replace exchange files with transcript forwarding
- do not assume access to another profile's local chat memory
- do not store specialist-local reasoning in exchange unless it belongs in the structured handoff itself

---

## Cleanup Rule

Do not aggressively delete exchange history by default.

Prefer:

- keeping structured history for audit
- separating examples from live outputs
- relying on type + subject + timestamp to identify the current valid artifact

If cleanup becomes necessary later, define an explicit archive policy first.

---

## Success Standard

This lifecycle is working when:

- the latest valid handoff is easy to identify
- examples are not mistaken for live work
- history remains readable without creating routing confusion
- specialists can exchange structured truth without transcript leakage
