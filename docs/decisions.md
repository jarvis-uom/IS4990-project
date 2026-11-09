# Decisions

Newest first. For each one, write the date, what we decided and why, so nobody has to remember it later.

## 2026-11-06 · What can be public

- **Decided:** our code can be public. Module A's code, protocols and results are published in the [Module A write-up](https://github.com/jarvis-uom/Mehara/tree/main/swot-tank-tracker/module-a). Never public: the Irrigation Department's storage tables, the survey data, index numbers and the trained models.
- **Why:** the project will be published in the end, and open code is easier to check. The department's tables are theirs to share, and part of the models' training data has no clear licence.

## 2026-11-05 · Module A: run 5 is the model, and a second series on fresh data

- **Decided:** run 5, a radar U-Net retrained on our own reservoirs, is Module A's model: it passed all four rules fixed before it was trained. A second series is judged only on data no model has seen: radar passes from 1 Nov 2026 to 31 Jan 2027 against the department's daily storage (scored in February 2027), 14 unused S1S2-Water scenes and an outside flood dataset.
- **Why:** run 5's tests had been used several times, so a claim needs tests that are new to every model.

## 2026-11-02 · How Module A is trained and checked

- **Decided:** no hand labelling. Training labels come from clear Sentinel-2 photos, and the maps are checked against expert-labelled datasets (Sen1Floods11, S1S2-Water), Google's Dynamic World and the department's daily storage. The rules of every training run are written down before it runs. Heavy computing runs on Kaggle.
- **Why:** examiners may not trust labels we draw ourselves, while expert datasets and storage records are independent. Rules fixed in advance stop us from picking whatever looks best afterwards.

## 2026-10-31 · Module owners confirmed

- **Decided:** Module A, AI water map (RQ1): [@mehara-rothila](https://github.com/mehara-rothila). Module B, SWOT heights, trust screen and storage model (RQ2, RQ3): [@dilshu09](https://github.com/dilshu09). Module C, forecast and system (RQ4): [@NimansalaBandara](https://github.com/NimansalaBandara).
- **Why:** each member presents and defends their own module at the proposal talk and in the thesis.

## 2026-10-31 · Backup topics moved out of this repo

- **Decided:** the Roadside Tree & Power-Line Risk Map and Paddy Land Watch proposals and briefs (4 PDFs) are removed from [proposals/](proposals/). They are kept, unchanged, in the team's private repo [jarvis-uom/backup-plans](https://github.com/jarvis-uom/backup-plans).
- **Why:** this repo now holds only the SWOT Tank Water Tracker project. This replaces the 27 Oct note that kept them here for reference.

## 2026-10-29 · Proposal approved

- **Decided:** both supervisors approved the **SWOT Tank Water Tracker** proposal.
- **The plan:** Member A, AI water maps (RQ1); Member B, SWOT heights, a trust screen and a storage model (RQ2, RQ3); Member C, the 2–4 week forecast and the system (RQ4).
- **Documents:** the final [proposal](proposals/swot-tank-water-tracker.pdf) and the [talk](presentation/). The eight village tanks are not one cascade (checked 29 Oct); their local names are still to be confirmed.

## 2026-10-27 · Target topic: SWOT Tank Water Tracker

- **Decided:** for now, our target topic is the **SWOT Tank Water Tracker**: the 5 big reservoirs east of Anuradhapura, plus 8 village tanks near Mahakanadarawa. The supervisor still has to approve the proposal.
- **Why:** the feasibility check said GO, with changes ([summary](research/swot-feasibility-check.md)). All the data we need is free, and the work splits into one research question each.
- The Roadside and Paddy proposals stay in [proposals/](proposals/) for reference. This closes [issue #1](https://github.com/jarvis-uom/is4990-project/issues/1).

## 2026-10-24 · Repo structure

- **Decided:** one main repo, `is4990-project`, for the final code, docs, tasks and weekly updates, plus a personal workspace repo for each member (`Mehara`, `Nimansala`, `Sewwandi`) for experiments.
- **Why:** everyone gets a free space to experiment, while the project stays in one place. Working results move into the main repo every week through a pull request, so nothing has to be merged at the last minute.

## 2026-10-22 · Team name and workspace

- **Decided:** the team name is **JARVIS**, written in capitals. We work in the GitHub organization `jarvis-uom`, in this repo, `is4990-project`.
- **Why:** one place for docs, tasks and code, with a history of who did what. The repo name stays neutral until we choose the topic; GitHub redirects the old link if we rename it.
