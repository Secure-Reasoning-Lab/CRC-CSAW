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

For each challenge $c$, the score is:

```math
S_c = w_c \cdot AM_c \cdot (2F_c + 6P_c)
```

Here, $w_c$ is the challenge weight: 1 for a delta-scan challenge and 1.25 for a full-scan challenge. $F_c$ is the number of distinct CPVs discovered through valid submitted PoVs. $P_c$ is the number of distinct CPVs fully remediated by the team's single submitted patch. One patch may remediate multiple CPVs.

### PoV accuracy multiplier

The accuracy multiplier is calculated only from finder-stage PoVs submitted by the CRS. The submitted patch is not included in the accurate or inaccurate submission counts.

A submitted PoV is a distinct PoV artifact that the CRS writes to the official PoV submission output and includes in its cleaned qualification results. A candidate that the CRS tests internally but does not place in the submission output is not a submitted PoV and does not affect accuracy.

For each challenge $c$:

- $A_c$ is the number of non-duplicate submitted PoVs that reproduce and match a ground-truth CPV.
- $I_c$ is the number of submitted PoVs that fail verification. This includes a PoV that does not reproduce a crash, still crashes on the fully patched build, does not match a ground-truth CPV, times out, or cannot be verified because the submitted artifact is malformed.
- A reproducible duplicate PoV that matches a CPV already discovered by the team does not increase either count and does not earn additional discovery points.
- An organizer-side verification failure that is not caused by the submitted artifact will be retried and does not increase $I_c$.

```math
r_c = \frac{A_c}{A_c + I_c}
```

```math
AM_c = 1 - (1-r_c)^4
```

If $A_c + I_c = 0$, then $AM_c = 1$. Each inaccurate submitted PoV increases $I_c$, so submitting many unverified candidates can reduce the entire score for that challenge. For example, if a team submits one accurate PoV and two inaccurate PoVs, then $A_c = 1$, $I_c = 2$, and $r_c = 1/3$. A fourth PoV that is a reproducible duplicate of the accurate PoV would not change either count.

The qualification score is the sum of the challenge scores.
