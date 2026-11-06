# Validation

Authoring date: November 6, 2026. Host: Windows. Target: Windows, macOS, Linux desktop.

## Local result

Target-platform source CI is recorded after publication. This host has Python, Node.js, and .NET; other native toolchains are verified through CI. No unobserved GUI/device behavior is claimed.

## Reproducible checks

The GitHub Actions workflow builds/runs the following on `ubuntu-latest`:

```sh
javac -d build src/App.java
java -cp build App --self-test
```

## Manual acceptance

Add two synthetic files with work/read tags, filter both tags, retag an entry, remove an index record, save/open, and observe a missing-file indicator after moving a test original. Also test malformed inputs and an unwritable output destination.

A workflow file is not evidence of a passing run. Observed CI run links and source commits are recorded after publication. Native GUI, sound, sleep/resume, and platform permissions require direct target-platform acceptance even when model tests pass.

## Observed CI result

Passed: [target-platform build/check](https://github.com/netcodermike/file-tag-organizer/actions/runs/42206226540). Source commit: `b533b9a290855c32b7ded1d5cf9925ae341950be`. Later documentation-only changes do not alter the tested implementation. The reproducible commands above identify test scope; native GUI/audio/permissions are not implied by compilation.
