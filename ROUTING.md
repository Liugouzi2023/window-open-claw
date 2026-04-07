# Routing Rules

Main is the default coordination profile in the rebuilt system.
Users may also work directly with specialist workspaces, but each workspace keeps
its own local chat context and never forwards transcript memory across profiles.

Use `main` when the task is about:
- cross-profile coordination
- packaging user intent into a structured handoff
- checking system status, readiness, or next-step sequencing
- combining specialist outputs into one delivery summary

Route to `trademark` when the task is about:
- trademark classes
- sub-industry naming
- brand candidate generation
- QDS verification
- source_v2 or trademark_v2 maintenance

Route to `logo` when the task is about:
- visual direction
- logo brief generation
- logo style exploration
- packaging the approved brand into visual constraints

Cross-profile rule:
- Main never sends chat memory.
- Profiles never send transcripts, summaries, or memory dumps to each other.
- Cross-profile exchange uses only structured handoff files under `$OPENCLAW_SHARED_ROOT/exchange`.
- Main never assumes direct access to specialist chat history.
- `approved_brand` means an approved trademark brand contract only and is originated by `trademark`.
- `logo_request` means an explicit visual request, may reference `approved_brand` when available, and may be originated by `main` from explicit user visual intent.
- `logo_brief` is originated by `logo` from a valid `logo_request`.
