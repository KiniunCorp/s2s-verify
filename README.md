# s2s-verify

Audits a git diff and reports what it observed, never what an agent claimed.

Your coding agent says the tests pass. `s2s-verify` runs them and reads the real exit code.
It says the feature is done. `s2s-verify` scans the diff for the shapes unfinished work leaves
behind, such as TODO markers and empty function bodies.

```
npx s2s-verify
```

Documentation: the [package README on npm](https://www.npmjs.com/package/s2s-verify) covers
every check, every finding kind, the verdict JSON schema and the limits.

To see it catch something first, run it on a repo with a planted bad commit:

```
git clone --depth 2 https://github.com/KiniunCorp/s2s-verify-demo demo && cd demo && npx --yes s2s-verify
```

## Formerly bramo-verify

This tool was published as `bramo-verify` up to 0.3.1. It is `s2s-verify` from 0.4.0, part of
the s2s (spec-to-ship) family.

- The new package still installs a `bramo-verify` command. It prints a one-line notice and
  then runs normally.
- Run `s2s-verify --install-hook` to replace a pre-push hook installed by bramo-verify.
- New verdicts are written to `.s2s/verdicts/`. Old ones stay in `.bramo/verdicts/`.
- The verdict JSON is now `schemaVersion: 3` with `"tool": "s2s-verify"`. No other field changed.

## What's in this repository

This repo is the public home for s2s-verify: releases, the issue tracker and, later, the GitHub
Action.

The engine's source is not here. s2s-verify is free to use but closed-source, and this repo
has no verification logic. We say so up front because a tool about honest reporting should be
honest about itself.

What we publish instead of the source is the method. The npm README documents each check and
the verdict schema, so you can judge a verdict without reading the code. An auditor works the
same way: it publishes its standards, not its software.

## Found a wrong finding?

Please open an issue. The tool is tuned to miss things rather than guess, so under-detection is
expected and over-detection is a bug. A finding on code that is fine is the failure we care
about most.

## Status

The CLI works and is documented. The GitHub Action is not built yet.

## Lineage

s2s-verify came out of s2s v1 (a private repo, formerly Bramo), which followed
[spec-to-ship](https://github.com/guschiriboga/spec-to-ship), s2s v0.

## History

This tool started as `bramo-verify`. Read the [post-mortem](docs/post-mortem.md) that explains why the larger Bramo platform stopped and only the verifier survived.
