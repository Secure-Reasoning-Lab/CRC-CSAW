# Qualification 2026

[qualification_set.tsv](qualification_set.tsv) contains the eight qualification benchmarks and their designated harnesses. Run every row with its listed scan mode and sanitizer. PCRE2 uses `undefined` (UBSan); the other rows use the default `address` sanitizer.

## Run

Complete the [CRC-Evaluate setup](https://github.com/Secure-Reasoning-Lab/CRC-Evaluate#readme), including dataset access, model configuration, and registration of your qualification CRS. The commands below reuse its default `.run/sanity` profile and `team-01` registration.

From the CRC-Evaluate repository root, run:

```bash
curl -fL https://raw.githubusercontent.com/Secure-Reasoning-Lab/CRC-CSAW/main/challenges/qualification-2026/qualification_set.tsv \
  -o .run/sanity/qualification_set.tsv

./scripts/run-queue/run-queue.sh --queue .run/sanity/qualification_set.tsv
```

The queue runner generates Finder/Patcher configurations, downloads and initializes missing benchmarks, and runs Finder then Patcher for each row. Results are saved under `.run/sanity/team-01/results/`. Run it in tmux for a long session.

For an existing custom setup, pass `--run-root YOUR_RUN_ROOT --team YOUR_TEAM_ID` to the runner. See the [run-queue documentation](https://github.com/Secure-Reasoning-Lab/CRC-Evaluate/blob/main/scripts/run-queue/README.md) for configuration, status, and resume options.

## Submit

Follow the [submission guide](../../SUBMISSION.md), clean and upload your result artifacts, and provide the download link and your CRC-Template repository link through the [qualification submission form](https://docs.google.com/forms/d/e/1FAIpQLSf3n2xBi0wo4F3GOIlbFJJBzTf0vhhCn10x3-EB5aNCDpKsBg/viewform).
