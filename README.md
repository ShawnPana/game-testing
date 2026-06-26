# game-testing

An agent skill for **human-style black-box playtesting of browser games**.

A tester agent that loads this skill plays a browser game the way a real gamer would — cold-start discovering the controls and mechanics by experimenting, playing the intended loop with real input, and judging whether the game is complete and feels right. It is a true black box: only the rendered screen + real input, no source/internal hooks, no per-game backdoors — so it generalizes to any browser game. It produces a recorded playthrough, an expected-flow narrative, and a structured `TEST_REPORT.md` verdict.

## Install

```sh
npx skills add <owner>/game-testing
```

(Replace `<owner>` with your GitHub user/org once pushed.)

## What it covers

- **Cold-start discovery** — figure out controls/mechanics yourself, then cross-check the manual
- **Genre instinct** — probe the verbs a gamer expects for the game's genre
- **Directed verification** — confirm specific behaviors when a "verify these" list is provided
- **Evidence** — a continuous gameplay recording, expected-flow, and a structured report

## Layout

```
skills/
└── game-testing/
    └── SKILL.md
```

## Notes / dependencies

- Recording uses **`ffmpeg`** (H.264 / `-pix_fmt yuv420p`).
- The skill drives the game via a CDP-style browser automation tool (e.g. browser-harness) with real keyboard/mouse.
- The "report your verdict" step is written for a multi-agent (tmux) setup; adapt the reporting transport to your own harness if different.

A companion `game-building` skill (builder-side rules) exists separately.
