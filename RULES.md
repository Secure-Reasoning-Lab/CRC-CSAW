# Competition Rules

## Team eligibility

Teams consist of one to four current college or university students and may list one advisor. A participant may belong to only one team.

## Autonomous operation

Scored vulnerability discovery and patch generation must be performed by the team's submitted cyber reasoning system. Human intervention is not allowed after a scored run begins.

## Allowed tools

Teams may use fuzzers, static or dynamic analysis, language models, agent systems, and other legally obtained tools. Teams are responsible for complying with the licenses and terms that apply to their tools and models.

Qualification submissions should use models from the [supported-model list](SUPPORTED_MODELS.md) so organizers can reproduce and evaluate the submitted CRS. Teams may use their own API providers for these models.

## Challenge scope

Competition targets and infrastructure may be used only for CRC@CSAW participation, research, and education. Do not attack competition infrastructure, other teams, external services, or systems outside the released challenge environment.

## Submission integrity

- Submit only artifacts produced for the registered team.
- Do not include credentials, private keys, access tokens, or personal data in submissions.
- Do not disable the harness, tests, build system, or vulnerable feature to obtain a passing result.
- Patches may modify only files permitted by the challenge statement.
- Organizer verification is authoritative.

## Qualification round

Qualification challenges will be released at a time to be announced on October 3, 2026. The qualification round lasts 48 hours.

At least 24 hours before the challenge release, each team must add the organizer GitHub account, to be announced, as a collaborator on the team's private repository created from or forked from [CRC-Template](https://github.com/Secure-Reasoning-Lab/CRC-Template). The repository must contain a branch named `qualification` with the CRS version the team will use for qualification. Teams may continue working on other branches, including `main`, but must not modify the `qualification` branch after the qualification CRS lock deadline. Commits made to that branch after the deadline will be ignored.

Organizers will inspect and reproduce top-scoring qualification submissions using the corresponding `qualification` branch. The audit will check whether:

1. the CRS prompts or code inject hints about a challenge solution;
2. the CRS is instructed or configured to search the web for a challenge solution; or
3. the submitted trajectory or reported results have been modified.

Organizers will run the CRS from the `qualification` branch up to three times. A team will be disqualified if the organizers cannot reproduce a result similar to the submitted result within those three runs or if the audit identifies any of the prohibited behavior above.

## Conduct

All participants must follow the [CSAW Code of Conduct](https://www.csaw.io/code-of-conduct).

Organizers may reject a submission or disqualify a team for violating these rules or compromising the fairness or safety of the competition.
