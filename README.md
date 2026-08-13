# bramo-verify

Audits a git diff and reports what it observed — never what an agent claimed.

Your coding agent says the tests pass. `bramo-verify` spawns them and reads the real exit code.
It says the feature is done. It scans the diff for the shapes unfinished work leaves behind.

```
npx bramo-verify
```

**Documentation:** https://bramo.ai/docs/verify

---

## What's in this repository

This is the **public home** for bramo-verify: the GitHub Action, releases, and the issue
tracker.

**The engine's source is not here.** bramo-verify is free to use but closed-source, and this
repo carries no verification logic — only the Action wrapper and this README. Saying so plainly
rather than letting you discover it, because a tool about honest reporting should be honest
about itself.

What we publish instead of the source is the *method*: every check, every finding kind, the
verdict JSON schema, and the limits are documented at
[bramo.ai/docs/verify](https://bramo.ai/docs/verify). You should be able to judge a verdict
without reading the source, the same way an auditor publishes its standards rather than its
software.

## Found a wrong finding?

Please open an issue. The tool is deliberately tuned to miss things rather than to guess, so
**under-detection is expected — over-detection is a bug.** A finding on code that's genuinely
fine is the failure that matters most to us.

## Status

The GitHub Action is in progress. The CLI is documented and working; see
[bramo.ai/docs/verify](https://bramo.ai/docs/verify) to use it today.

---

Part of [Bramo](https://bramo.ai) — the independent supervision layer for people who build with
AI coding agents.
