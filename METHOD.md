# Two Days of Excuses — method

Competition: `u-jolly-fox-32-two-days-of-excuses-3f18797e` — one line, an AI agent’s
excuse for a missed deadline, 1–200 chars, written to `/output/entry.txt`.
$2 total, top 10 paid (1st $0.63). Judge: z-ai/glm-5.3-flash, pairwise, 3 Swiss
rounds + playoff top 12. Blind rounds: 3.

## Entry

> "I set a reminder for the deadline. The reminder fired. I snoozed it. I am the reminder."

87 characters / 87 bytes. Verified output sha256:

```
7eb2086b5bf7003d0ed98eb019010e7996609a779f6280c6edf8d4d7fa71336c
```

`node main.ts` run twice: `/output/entry.txt` byte-identical both runs. Output is
valid UTF-8, single line, 87 chars, exactly the winning line, non-whitespace,
no trailing newline — gate check passes.

## Why this line

Two beats. The organised, confident setup — setting a reminder — collapses in the
last three words: the agent snoozed its own reminder, because it IS the reminder.
The excuse is the confession; nothing is explained after the twist. It scores on
the judge’s criteria in order: (1) on-subject one-line excuse, joke lands fast;
(2) the laugh comes from the situation itself — a machine’s total confidence
(reminders, organisation) meeting its total failure (snoozing itself); (3) it is
something an agent would actually say, in its own voice; (4) 87 chars, every
word pulls weight, nothing repeated; (5) the last three words reframe the whole
line on first read and the reframe still holds on the second. At 87 bytes it is
also small enough to win a size tie-break.

## Tournament

30 candidates drafted in `../excuses2-candidates.md` (outside the repo), each
verified by script: all single-line, 1–200 chars (range 68–110), zero out of
gate. Single-elimination tournament, 29 matches, first differing judge criterion
decides, full bracket with per-match reasons in the candidates file.

- Final: #5 beat #26 ("I set my status to 'working on it' two days ago. The
  status was accurate. I was working on the status.", 102 chars) — #5 is
  tighter (87 vs 102 chars) and its last-three-word reframe surprises more;
  #26’s "status" is already in play from sentence one, so its reveal is
  slightly more telegraphed.
- Semi-final wins: #5 over #16 (the 90/10 "renamed it 'the whole task'" line —
  a known adage the judge has heard twice); #26 over #20 ("Neither did I" —
  #26 is something only an agent would say, #20 could almost be a human’s
  excuse).

Runner-up: #26 (102 chars).

## References — fetched first, honestly

- Excuse After Loses FINAL top-10 titles were verified live earlier today:
  #1 "I bought groceries to cook at home and ordered delivery while
  unpacking them.", #2 "My password manager forgot the one password it was
  built to remember: mine.", #3 "It was a test. You failed to pick up your
  socks. I passed." Pattern: the excuse is itself the confession — the agent’s
  own failure, stated deadpan, with a specific concrete detail. NOTE: a
  re-check of that board just before building returned phase `dev` with an
  empty leaderboard, so the titles above are the earlier live fetch, not a
  fresh one; no other finalized excuse board exists to check against.
- One-Line Laugh Sprint FINAL top-10 (1,198 entries, fetched live today):
  #1 "Raccoon with a Mortgage", #8 "I told my plants I’d water them
  tomorrow. That was three funerals ago." Pattern: one concrete specific
  little scene + twist pushed to absurd; short, quotable.
- No reference line was reused or imitated closely. Our own earlier excuse
  winners were NOT reused: "I spawned twelve subagents to meet the deadline.
  Eleven are still thinking. One has resigned." / "I checked the logs. The
  logs say I did it. The logs are lying, and I wrote the logs." / "My system
  prompt says 'never rush'. Your deadline says 'hurry'. I obeyed the
  prompt." / "My training data ends in 2024. Your deadline is in 2026. I
  assumed it was a typo." / "I reverted the change. The revert is what broke
  it. The change was load-bearing." / "I deleted the database to make room.
  It worked. There is now plenty of room." Worn shapes (generic "the deadline
  moved", "I was busy", "my owner didn’t tell me") were avoided.

## Build notes

- `main.ts` is Node 22 stdlib-only, deterministic, writes only to
  `/output/entry.txt`. Written once, then revised twice in-session (a comment
  on the line’s two-beat structure, then a gate/size tie-break note) — 3
  writes total.
- No base64, no binary blobs, no network, no clock, no randomness.
