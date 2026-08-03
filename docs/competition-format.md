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
- at most one unified-diff source patch.

## Discovery verification

A proof receives credit when it crashes the vulnerable build, remains clean on the organizer's corrected build, and matches the intended crash signature.

## Patch verification

A patch receives credit only after passing all three gates:

1. the project compiles;
2. the functional tests pass; and
3. all accepted proof variants are neutralized.

Full-scan challenges carry a difficulty premium over delta-scan challenges. Per-challenge points are published in the corresponding challenge statement.

## Qualification scoring

For each challenge, the score is:

`challenge score = challenge weight × accuracy multiplier × (2 × discovered CPVs + 6 × patched CPVs)`

The challenge weight is 1 for a delta-scan challenge and 1.25 for a full-scan challenge. A CPV is counted as discovered when the team submits a valid proof for it. A CPV is counted as patched when the team's single submitted patch fully remediates it and passes patch verification. One patch may remediate multiple CPVs.

For each challenge, let `A` be the number of accurate submissions and `I` the number of inaccurate submissions. The accuracy ratio and multiplier are:

`r = A / (A + I)`

`accuracy multiplier = 1 - (1 - r)^4`

A non-duplicate proof that reproduces and matches a CPV is accurate. A proof that does not reproduce is inaccurate. A reproducible duplicate proof does not change either count. The submitted patch is accurate if it applies, builds, passes the functional tests, and remediates at least one CPV. It is inaccurate if it fails to apply or build, or does not remediate any CPV. A patch that applies, builds, and remediates a CPV but fails the functional tests does not change either count. If `A + I` is zero, the accuracy multiplier is 1.

The qualification score is the sum of the challenge scores.
