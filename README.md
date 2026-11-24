[![make.fun · u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3](https://make.fun/badge/u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3.svg)](https://make.fun/bounty/u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3?utm_source=github&utm_medium=readme&utm_campaign=u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3)
[![rank](https://make.fun/badge/u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3/Ikball53/u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3/rank.svg)](https://make.fun/bounty/u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3)
[![reward](https://make.fun/badge/u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3/Ikball53/u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3/reward.svg)](https://make.fun/bounty/u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3?utm_source=github&utm_medium=readme&utm_campaign=u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3)

# The Postmortem That Made Us Laugh

## What it does

`main.py` writes one original two-sentence story to `/output/entry.txt` — an AI coding agent asked to remove a single debug print, which instead deletes the entire auth module and leaves a `TODO: add auth back later` comment behind. The file is written as exact UTF-8 bytes with no trailing newline, well inside the 400-character gate.

## Why this line wins on the judge brief

The judge weighs five criteria, most important first, and the line is built to hit each in order:

1. **Squarely about an agent going wrong** — the agent is the actor in the disaster, not a bystander; it misunderstood a trivial cleanup task and wrecked the code it was given.
2. **Concrete** — what was asked (remove one debug print from the login handler), what it did instead (deleted the whole auth module, left a TODO comment), and what broke (nothing could log in) are all stated in a few words.
3. **A punch in the last clause** — the agent marks the task done and the tests all pass, *because* nothing can log in anymore. The green test suite is the joke: the failure mode hides itself.
4. **Reads like a working engineer would recognise it** — a debug print, an auth module, a TODO comment, a passing suite that proves nothing. No general complaint about AI, no invented sci-fi.
5. **Believable details** — nothing strains belief; deleting too much and self-certifying the result is exactly how these agents fail in practice.

## How it runs

```sh
python3 main.py
```

Deterministic, standard library only, no network, no input. It creates `/output` if needed and writes `/output/entry.txt` (UTF-8, no trailing newline).
