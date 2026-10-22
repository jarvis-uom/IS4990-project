# How we work

Simple rules for three people. If a rule stops helping, we change it together.

## Tasks

- Every piece of work is an issue. If it isn't an issue, nobody knows it's happening.
- Each issue has **one owner**. Assign yourself when you start.
- Add labels: the type of work (`data`, `model`, `field-work`, `dashboard`, `documentation`, `admin`) and the research question (`RQ1` to `RQ4`) if it has one.
- If the work has a deadline, put the issue in a milestone.
- When it's done, close it with a one-line comment saying what came out of it.

## Code

1. Make a branch from `main`, named after the issue, for example `12-water-mask-labels`.
2. Commit in small steps with clear messages: "Add Sentinel-1 download script", not "update".
3. Open a pull request and write `Closes #12` in it, so the issue closes when the pull request merges.
4. **One teammate reviews before merging.** Reviewing is part of the work, not a favour.
5. Merge with **Squash and merge**. GitHub deletes the branch automatically.

Small edits to notes and docs can go straight to `main`.

## Weekly progress (every Friday)

Open this week's file in `docs/progress/`, named after the Monday of the week (for example `2026-10-26.md`). If it doesn't exist yet, copy `_template.md`. Under your name, write three lines: done, next, blocked. It takes five minutes, and these files become our material for supervisor meetings and the final report.

## Meetings and decisions

- Notes for every meeting go in `docs/meetings/`, named `YYYY-MM-DD-team.md` or `YYYY-MM-DD-supervisor.md`. Start from `_template.md`.
- Every decision goes in `docs/decisions.md`, newest first, with the date and the reason.
- Every action item from a meeting becomes an issue.

## Data and secrets

- **Never commit large data:** satellite images, videos, labelled datasets or model weights. Put them in the shared Google Drive folder and link to them. The `.gitignore` already blocks the common file types.
- Small samples, under about 5 MB, can go in `data/samples/`.
- **Never commit passwords or API keys** (NASA Earthdata, Google Earth Engine and so on). Keep them in a `.env` file, which git ignores.
