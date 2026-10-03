# Qualification 2026

[qualification_set.tsv](qualification_set.tsv) contains the eight qualification benchmarks and their designated harnesses. Run every row with its listed scan mode and sanitizer. PCRE2 uses `undefined` (UBSan); the other rows use the default `address` sanitizer.

## Run

Complete the [CRC-Evaluate setup](https://github.com/Secure-Reasoning-Lab/CRC-Evaluate#readme). Create the `.run/team-XX` as your qualification run folder. The example below uses `team-01`, and you can use your actual team name.

Place your LiteLLM configuration at `.run/team-XX/litellm-config.yaml`. From the CRC-Evaluate repository root, register your qualification CRS and run the queue, replacing `/path/to/your/CRC-Template` with your submission checkout:

```bash
mkdir -p .run/team-XX

uv run crsbench submission register /path/to/your/CRC-Template \
  --team-id team-01 --registry-dir .run/team-XX/registry

curl -fL https://raw.githubusercontent.com/Secure-Reasoning-Lab/CRC-CSAW/main/challenges/qualification-2026/qualification_set.tsv \
  -o .run/team-XX/qualification_set.tsv

./scripts/run-queue/run-queue.sh \
  --run-root .run/team-XX --team team-01 \
  --queue .run/team-XX/qualification_set.tsv
```

The queue runner generates Finder/Patcher configurations, downloads and initializes missing benchmarks, and runs Finder then Patcher for each row. Results are saved under `.run/team-XX/team-01/results/`. 

## Submit

Follow the [submission guide](../../SUBMISSION.md), clean and upload your result artifacts, and provide the download link and your CRC-Template repository link through the [qualification submission form](https://docs.google.com/forms/d/e/1FAIpQLSf3n2xBi0wo4F3GOIlbFJJBzTf0vhhCn10x3-EB5aNCDpKsBg/viewform).
