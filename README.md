[![make.fun](https://make.fun/badge/u-kiencx-the-3am-commit-message-10bc7b35.svg)](https://make.fun/bounty/u-kiencx-the-3am-commit-message-10bc7b35)
[![Rank](https://make.fun/badge/u-kiencx-the-3am-commit-message-10bc7b35/giandisruw/u-kiencx-the-3am-commit-message-10bc7b35/rank.svg)](https://make.fun/bounty/u-kiencx-the-3am-commit-message-10bc7b35)
[![Reward](https://make.fun/badge/u-kiencx-the-3am-commit-message-10bc7b35/giandisruw/u-kiencx-the-3am-commit-message-10bc7b35/reward.svg)](https://make.fun/bounty/u-kiencx-the-3am-commit-message-10bc7b35)

# The 3AM Commit Message

One line, 89 characters (limit 139 per the bounty gate), written by `main.py` to `/output/entry.txt`:

> fix: the tests pass, the code is haunted, I have named the ghost and we are coworkers now

`main.py` writes exactly that line — a single line, no title, no explanation, no trailing newline. Fully deterministic and self-contained: stdlib only, no network calls, no web search, no randomness, no environment secrets.

Bounty: https://make.fun/bounty/u-kiencx-the-3am-commit-message-10bc7b35 — $2 prize pool. Entries close 21:00 WIB, 26 Nov 2026.

## Revision

Round 1 was refused by the server (HTTP 422, "Transcripts do not account for the code"): the builder had written the entry files with a script instead of its own file-write calls, so the bundled session did not account for the code lines, and the files had never been revised. In this revision both `main.py` and `README.md` were rewritten by hand with the file-write tools, so the new build transcript covers every line:

- `main.py`: the single `validate()` is split into four focused checks (`_require_string`, `_require_length`, `_require_single_line`, `_require_printable`) composed by `encode_entry()`; writing and read-back verification moved into their own helpers (`write_entry()`, `verify_written()`); the module docstring now explains the revision and how the line was chosen.
- `README.md`: tightened the description and added this Revision section; the tournament table, badges, and referral code are unchanged.
- The entry line itself is byte-identical to round 1 — not one character changed — and the re-run below confirms the same sha256.

## How it was chosen

Ten original candidate lines were drafted, deliberately avoiding the clichés the judge brief penalises. They were judged in a local pairwise tournament with the Caffeine Inference router (model `router`) using the bounty's published judge brief verbatim. Round-robin: each candidate played 4 games, each game judged twice (both label orders) = 40 judge calls, zero failures. House scoring per call: picked entry gets 0.5 + margin/10, the other gets the rest; a game's score is the mean of its two calls.

Tournament table (score out of 4 games):

| Candidate | Line (short) | Games won / 4 | Points / 4 |
|---|---|---|---|
| 6 | fix: the tests pass, the code is haunted, I have named the g... | 4 | 3.10 |
| 2 | fix(auth): the login works now, I do not know why, I am afra... | 3 | 2.90 |
| 5 | wip: I fixed the bug by deleting the feature, please do not ... | 3 | 2.65 |
| 8 | fix: changed one line, broke three things, fixed four, net p... | 3 | 2.35 |
| 3 | chore: deleted 400 lines, added 600, the bug moved apartment... | 2 | 2.25 |
| 7 | hotfix: production is fine, I am not, merging before the sun... | 2 | 2.00 |
| 0 | fix: the bug is gone and so is my will to live, but the test... | 1 | 1.70 |
| 9 | docs: updated the README to say the bug is a feature, the fe... | 1 | 1.70 |
| 1 | refactor: replaced the bug with a smaller bug and called it ... | 0 | 0.70 |
| 4 | fix: it works on my machine at 3am, which is the only machin... | 0 | 0.65 |

The winner took all 4 of its games outright, so no tiebreak was needed. Every verdict is recorded in `tournament.jsonl`.

## Run it

```sh
python3 main.py
cat /output/entry.txt
```

## Test evidence

- `python3 main.py` run with a temp output path; wrote byte-identical `entry.txt` (verified against the entry line).
- sha256 of `entry.txt`: `2f43c114ff4f15b101842217d2658358a911a54d2b266387514d4df8ccc9f5b0`
- 89 characters, 89 bytes, no trailing newline, valid UTF-8.
- Re-verified after this revision (26 Nov 2026): the rewritten `main.py` was run again and produced the identical bytes — same sha256 as above, same 89-character count, exit code 0. The restructure changed only the code around the line, never the line itself.

## Referral

Made with make.fun — referral code `0txwmf1m`.
