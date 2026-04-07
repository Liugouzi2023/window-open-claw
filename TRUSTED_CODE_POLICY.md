# Trusted Code Policy

## Purpose

Define how this system treats skills, plugins, scripts, and other executable additions.

This policy exists to reduce accidental trust expansion.
The system should not rely on vague intuition when deciding whether code is safe to install, keep active, or promote into regular use.

---

## Core Rule

Treat all non-core executable additions as untrusted until reviewed.

That includes:

- third-party skills
- third-party plugins
- downloaded scripts
- hook code
- helper binaries
- copied snippets that execute code or send data

Default stance:

- not trusted by default
- not auto-enabled by default
- review before regular use

---

## Trust Classes

### Class A — Core local system files

Examples:

- current workspace files already owned by this system
- approved local operating files
- existing coordinator documents

Default stance:

- trusted for intended local use
- still subject to boundary rules

### Class B — Official upstream code

Examples:

- official OpenClaw docs
- official OpenClaw CLI behavior
- official OpenClaw repository materials
- official provider docs/repos

Default stance:

- preferred source of truth
- verify relevance and version before acting

### Class C — Self-authored local code

Examples:

- code written intentionally for this system
- local scripts created during system setup
- profile-local operational files created on purpose

Default stance:

- conditionally trusted
- must still be understandable, scoped, and reviewable

### Class D — Third-party reviewed additions

Examples:

- a third-party skill kept after explicit review
- a plugin whose behavior and source have been examined
- a script retained after security and scope review

Default stance:

- usable, but still monitored
- trust is explicit, not assumed

### Class E — Third-party unreviewed additions

Examples:

- newly discovered skills from hubs/registries
- copied scripts from random repositories
- hook packages not yet examined

Default stance:

- untrusted
- do not auto-enable
- do not treat as system-native

---

## Review Triggers

A code artifact must be reviewed before regular use if any of the following are true:

- reads environment variables or secrets
- sends network requests
- writes outside the workspace without a strong reason
- adds hooks or automatic execution paths
- alters routing, memory, config, or startup behavior
- runs package install or post-install logic
- introduces cross-session or cross-profile effects
- is intended to become persistent or default behavior

---

## High-Risk Patterns

Treat these as high-risk until explicitly cleared:

- env access + network send
- automatic hooks
- silent background execution
- broad file writes
- credential handling
- browser/session scraping
- cross-profile memory movement
- code that modifies core rule files automatically

High-risk code should not be enabled by default.

---

## Approval Rule

Before making nontrivial third-party code part of the regular system, decide one of:

1. reject
2. isolate
3. review and keep as limited-use
4. promote to trusted regular use

If the answer is unclear, do not promote it.

---

## Activation Rule

Unreviewed third-party code must not be:

- auto-loaded as default behavior
- attached to startup hooks by default
- silently granted broad filesystem or network trust
- treated as equivalent to official platform behavior

---

## Recording Rule

When a code artifact is reviewed, record at minimum:

- what it is
- where it came from
- why it is needed
- what risk class it falls into
- whether it is active, isolated, or disabled

This can be tracked in a simple local review note if needed.

---

## Current System Example

Example already seen in this system:

- `openrouter-models` was flagged by OpenClaw security audit for env access + network send pattern
- correct response was not to assume safety
- it was removed from active skills and isolated from regular use

This is the expected policy behavior.

---

## Success Standard

This policy is working when:

- third-party code is not trusted by accident
- risky additions are reviewed before regular use
- automatic execution paths are treated carefully
- system trust grows deliberately, not casually
