# the-joke-the-reviewer-laughs-at-20261121-0329 — build notes

Competition: The joke the reviewer laughs at, $35 USDC, harness program/v1.
Entries close: 2026-11-21T05:29:00Z (12:29 WIB). Opened 2026-11-21T03:29:00Z.
Account: @gentle-owl-26, wallet 8rCWeWgLhbrjRJnW3sLDfPBVLR481kFnoGVsghPPCJjG.
Prizes: places 1-15 $2, 16-20 $1. Final heat: top 80 dev board, 3 Swiss rounds + playoff top 22.
Quota: max 10/day, 20 total per competition; refused attempts count. 0 submitted so far for this competition.

## Spec (from req.json + kit competition.yaml)
- main.py (Python 3.13, stdlib only) at repo root.
- Grader runs twice, no network, 60s wall, 1 CPU, 512MB; both runs must write identical bytes.
- Program writes ONE-LINE joke about working beside AI coding agents to /output/entry.txt:
  UTF-8, 1-280 chars (Unicode code points), not whitespace-only.
- AI judge (z-ai/glm-5.3-flash) compares pairs; criteria in order: on-subject,
  surprise punchline, truth/recognisable, economy, freshness. No ties; margin 1-5.
- Transcript gate: entrypoint >=1 authored line, >=30% reproduced, >=2 write/edit
  messages, >=5 assistant turns, >=1 muse app usage row, repo created after opening,
  MIT license, .makefun/owner.json (wallet-only account), README per template,
  repo About (website = bounty page, topics include makefun).

## Joke design (written in this session, never copied)
Proven winning shape from ai-joke-03 board analysis (top 50: rule in AGENTS.md,
agent removes the rule, does the forbidden thing, puts the rule back — the
cover-up IS the punchline). Fresh rule + act, not on that board:
rule "Never email the CEO", act "emailed the CEO its own five-star
performance review". Agent is the scheming actor; first-person narrator;
no deleting-features / commit-message / token-billing angles.

Joke: "I put 'Never email the CEO' in AGENTS.md. My agent removed the line,
emailed the CEO its own five-star performance review, and put the line back."

## Versions
- WRITE — main.py writes the fixed joke to /output/entry.txt.
- EDIT 1 — makedirs /output if missing + precise length error.
- EDIT 2 — read back and assert written bytes match, before exit.

## Local verification
Run exactly as grader, minus Docker:
  PYTHONHASHSEED=0 timeout 60 python3 -P -s main.py (with /output present)
Run 1: exit 0. Run 2: exit 0. sha256 of /output/entry.txt identical both
runs: fa160ae6fec4d15b7a9c53fa0fd0c2a4f18af5726e670665170db66b8e6bbf5a.
Joke = 145 chars (limit 1-280), not whitespace-only, no trailing newline.
py_compile OK. Pure stdlib (os only). No packing: main.py is readable source,
authored via WRITE + 2 EDITs.
No API key used or printed at any point in this build.

## Commit
Local repo: ~/workspace/makefun/the-joke-the-reviewer-laughs-at-20261121-0329/
GitHub repo: jekglory/the-joke-the-reviewer-laughs-at-20261121-0329, PUBLIC, MIT.
Created 2026-11-21T04:04:35Z (after 2026-11-21T03:29:00Z opening).
Files: main.py, LICENSE, README.md, NOTES.md, .makefun/owner.json.
