# Competition Format

CRC@CSAW uses a find-then-patch workflow based on the OSS-CRS and CRSBench ecosystem.

## Challenge package

Each challenge provides:

- a vulnerable open-source project revision;
- one designated fuzzing harness;
- build tooling and a functional test suite; and
- for delta-scan challenges, the bug-inducing change as a diff.

Organizer ground truth, reference proofs, reference patches, and scoring metadata remain private.

## Team outputs

For each challenge, a team produces:

- one or more proof-of-vulnerability inputs; and
- a unified-diff source patch.

## Discovery verification

A proof receives credit when it crashes the vulnerable build, remains clean on the organizer's corrected build, and matches the intended crash signature.

## Patch verification

A patch receives credit only after passing all three gates:

1. the project compiles;
2. the functional tests pass; and
3. all accepted proof variants are neutralized.

Full-scan challenges carry a difficulty premium over delta-scan challenges. Per-challenge points are published in the corresponding challenge statement.
