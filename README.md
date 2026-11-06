# File Tag Organizer

Maintain a local file-path/tag index with AND filtering and portable saves.

[![Build and verify](https://github.com/netcodermike/file-tag-organizer/actions/workflows/verify.yml/badge.svg)](https://github.com/netcodermike/file-tag-organizer/actions/workflows/verify.yml)

**Language:** Java · **Platform:** Windows, macOS, Linux desktop · **App type:** Desktop file tagging and saved search app

First-release learning implementation, with explicit scope below. This is one independently runnable app, not a placeholder in a combined repository.

## Features

- File picker and retagging
- Normalized comma-separated tags
- Missing-file indicators
- Explicit index save/open

## Requirements

JDK 17+ and Swing for desktop use; self-tests run headlessly. No external packages.

## Quick start

```sh
git clone https://github.com/netcodermike/file-tag-organizer.git
cd file-tag-organizer
javac -d build src/App.java
java -cp build App
```

Commands run from the repository root. Lines marked for a particular operating system apply only there. Language tools are prerequisites, not installed by the app. Close desktop windows normally; terminal/server apps stop with Ctrl+C unless their usage notes say otherwise.

## Example workflow

Add two synthetic files with work/read tags, filter both tags, retag an entry, remove an index record, save/open, and observe a missing-file indicator after moving a test original.

## Architecture, configuration, and data

App.java stores absolute file paths mapped to normalized lower-case tag sets. Queries require all entered tags. Properties keys encode UTF-8 paths in Base64, with comma-separated tag values; this is encoding, not encryption. Index entries are capped at 5,000 and tag sets at 30. Tests validate normalization and serialization. Original files are not moved, renamed, opened, or modified.

## Verification

Build with the quick-start command where needed, then run:

```sh
java -cp build App --self-test
```

Manual acceptance: Add two synthetic files with work/read tags, filter both tags, retag an entry, remove an index record, save/open, and observe a missing-file indicator after moving a test original. Also test malformed inputs and an unwritable output destination.

See [validation record](docs/VALIDATION.md) for observed checks and their limits. CI results verify only what the workflow runs; they do not establish native GUI correctness or production readiness.

## Limitations and next steps

No content search, filesystem watching, rename tracking, path relocation, encryption, automatic save, or embedded file metadata. Commas separate tags and cannot appear inside a tag. Closing loses unsaved index changes. Paths may reveal private information; save only where intended.

## Troubleshooting

Use the exact platform/toolchain above. Preserve originals and use synthetic fixtures first. Errors are displayed in the UI or stderr. A headless machine can run the model tests but cannot verify native GUI/audio behavior. Output paths are chosen explicitly; keep backups of important data.

## Source map

- `src/App.java`

## Development and license

Read [contributing](CONTRIBUTING.md) before changing the app, and [security/privacy](SECURITY.md) before supplying private data. Use synthetic fixtures for tests. No telemetry, paid API key, or account is required by the app itself. Dependencies, when present, are stated in Requirements.

[MIT license](LICENSE), copyright 2026 netcodermike.
