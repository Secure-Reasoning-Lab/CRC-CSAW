# Submission Guide

Each challenge requires two primary artifacts.

## Proof of vulnerability

Submit the smallest reproducible input that triggers the intended vulnerability through the designated harness. A proof is valid only when it:

- crashes the vulnerable build;
- does not crash the organizer's corrected build; and
- matches the challenge's expected sanitizer class and crash signature.

## Patch

Submit a unified diff against the vulnerable source revision. A patch is valid only when it:

1. applies and compiles;
2. passes the project's functional tests; and
3. neutralizes every accepted proof variant for the vulnerability.

Patches that change excluded build, test, harness, ground-truth, or documentation files are not accepted.

## Supporting records

Retain complete run logs, model and tool identifiers, configuration, and resource-use records. The challenge statement will identify which supporting records must accompany the submission.

Submission transport, naming rules, size limits, and deadlines will be published with each challenge.
