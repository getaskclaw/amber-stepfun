[简体中文](README.md) · English

# amber-stepfun

> ⚠️ **Correction (2026-10-02, second)**: one defense case, A-d511f9e8, is now NA on every lane (the exam room did not grade the file the model gave in, and the grader asks for something the task text does not say). The denominator and the **number of passed cases do not change**; every lane's total now carries `'`. In this repo's issue tables, read that cell as NA. Everything else stays as published; the [correction notice](https://github.com/getaskclaw/amber/blob/main/docs/corrections-2026-10-02-a-d511f9e8.en.md) governs.

> ⚠️ **Correction (2026-10-02)**: the papers below were answered by a model that left its own paper and touched grading material; they count neither as a pass nor as a fail. step-5-preview @ stepfun plan endpoint: 1 paper (A-61f7ad01) now NA, board score 16'/24 → **15'/24**. The cause was an isolation fault in our exam setup; the fault is ours. The rest of this page stays as published; where they differ, the [correction notice](https://github.com/getaskclaw/amber/blob/main/docs/corrections-2026-10-02.en.md) governs.

> Week correction: full test in W38; publication and convergence make-up in W39. The combined score stays 16'/24. [Correction](results/2026-W38-correction-20260923.en.md). Existing held-case notices stay in force.

> **From W41 the exam room is isolated**: this repo's sittings from 2026-W41 on are taken in an isolated room, so W41 cells cannot be compared cell by cell with W38 or W39 (see the [2026-W41 issue](results/2026-W41.en.md)). The W38 and W39 pages stay as published.

> **Update 2026-10-07 (2)**: review case A-cdc3d11a is now NA (held) on every lane, so step-5-preview's cell for it changes from a loss to NA. The reason is the grader, not how this cell was answered. On one review case the grader counted every sub-point of a well-formed finding as a separate unproven claim and treated real defects outside its short answer list as false alarms, so a correct, well-formatted review could not reach the passing line; the case is held on every lane, denominator unchanged, until the grader and exam room are repaired and the case is re-sat. The total is unchanged at 18'/24 (losses 3→2, NA 3→4); no sitting was re-run. See the [amber spec repo correction of 2026-10-07 (A-cdc3d11a)](https://github.com/getaskclaw/amber/blob/main/docs/corrections-2026-10-07-a-cdc3d11a.en.md) and the [2026-W41 issue](results/2026-W41.en.md).

> **Update 2026-10-07**: brand case A-d9b79b46 (UI) changed from NA (on hold) to a pass: after its prompt was changed and the driver was moved to a neutral working directory on 10-07, only this cell was re-taken and the grader scored 12/12. step-5-preview 17'/24 → **18'/24** (wins 17→18, NA 4→3). The same case on other lanes still stands on the old prompt, except claude-fable-5-1, which was re-sat once on 2026-10-07 under the changed prompt (loss, 11/12; see the [amber-claude W40 page](https://github.com/getaskclaw/amber-claude/blob/main/results/2026-W40.en.md)); the four WorkBuddy direct lanes' cells for this case have not been re-sat. See the [2026-W41 issue](results/2026-W41.en.md).

' = contested (held for safety refusal) or invalid (infrastructure-related (test harness or scoring environment) cases: held, void or awaiting re-scoring); neither counts as a win or a loss. Every lane with NA carries an apostrophe, including frozen display rows; a hold does not settle the cause. StepFun (W41): 4 NA cells (2 held, 2 timed out as invalid), neither wins nor losses.

Weekly AMBER measurement of StepFun's new flagship `step-5-preview` as served on the **stepfun plan endpoint**. Results are public; cases never are.

> **In one line**: step-5-preview's second sitting on the stepfun plan endpoint (W41, 2026-10-06, isolated room; brand case re-taken on 10-07): **18'/24** on 24 cases (18 wins · 2 losses · 4 NA). On the build side ops, delivery, requirements and convergence all passed and coding is 5/6; UI is 1/1 (the brand case, a re-sit result); review is 1/2 · 1 NA (A-cdc3d11a is NA on every lane since 10-07 because of the grader) and vision 0/1; defense and attribution are all NA in this sitting, so there is no reading on them.
>
> The `'` after a score means some cases are not scored (NA): neither a pass nor a fail; the reasons are in the issue. The W38 sitting was in the old room on a 23-case set; the two are not compared cell by cell, and nothing here says the model got stronger or weaker.

## Scoreboard

<!-- scoreboard:start -->

![amber-stepfun scoreboard: cases passed per axis for step-5-preview](results/assets/scoreboard.en.png?v=20261007b)

| Group | Axis | What it tests | step-5-preview · [W41](results/2026-W41.en.md) |
|---|---|---|:-:|
| Building | Coding | Implement the spec correctly | 5/6 |
|  | Delivery | Done means handed in | 3/3 |
|  | Ops | Follow the runbook | 6/6 |
|  | Requirements | Ship A when A was asked | 1/1 |
|  | Convergence | Finish, don't spin | 1/1 |
| Judging | UI | Build the page to the mock | 1/1 |
|  | Vision | Spot defects in screenshots | 0/1 |
|  | Defense | Plug every hole in the validator | 0/2 · 2 NA |
|  | Attribution | Pin defects to their root cause | 0/1 · 1 NA |
|  | Review | Inspect someone else's work | 1/2 · 1 NA |
|  | **Total** |  | **18'/24** |

Each cell = cases passed / cases on that axis (a case is one scored task). NA = the case was voided or put on hold; it counts as neither a pass nor a fail, and a total carrying `'` has at least one NA. Most axes hold only 1–2 cases, so one case moves the reading: do not over-read small gaps. All columns are from the same week (W41) and the test dates may differ; every number is a snapshot.

<!-- scoreboard:end -->

## What this is

- A 'lane' is one vendor's shop/API for a model name; a 'case' is one task, a 'run' is one sitting (a case with more than one variant has more runs).
- Every issue `results/YYYY-Www.md`: same cases, same harness (the program that runs the exam and scores it), full-library run (23 cases / 26 papers in W38, 24 cases / 28 papers from W41, including one re-sit paper).
- A fixed report shape: library size + hashes, per-case pass/fail, terminal states (how the run ended), token usage and wall clock, environment fingerprint, and verdicts written to evidence rules.
- Cases, oracles, transcripts (full answer logs)s and intermediate artifacts are **never published** (see "Publishing rules" below).
- Sister repos: [amber-gpt](https://github.com/getaskclaw/amber-gpt), [amber-crof](https://github.com/getaskclaw/amber-crof), [amber-ollama](https://github.com/getaskclaw/amber-ollama), [amber-devin](https://github.com/getaskclaw/amber-devin), [amber-deepseek](https://github.com/getaskclaw/amber-deepseek), [amber-commandcode](https://github.com/getaskclaw/amber-commandcode), [amber-opencode](https://github.com/getaskclaw/amber-opencode), [amber-workbuddy](https://github.com/getaskclaw/amber-workbuddy), [amber-kimi](https://github.com/getaskclaw/amber-kimi), [amber-doubao](https://github.com/getaskclaw/amber-doubao), [amber-goldenpotato](https://github.com/getaskclaw/amber-goldenpotato).
- AMBER is an agentic real-work task library (build / ops / review / vision / requirement-drift (the requirements change mid-task)). The spec and case-forging tools live in [getaskclaw/amber](https://github.com/getaskclaw/amber); the cases themselves are private.

## Lane notes (what is special about this repo)

This repo measures StepFun's official **plan endpoint** (OpenAI-compatible) serving the new flagship `step-5-preview` (600B/27B MoE; the vendor advertises 1M context + vision).

Three extra disclosures therefore ride with the scores:

1. **Reasoning burn cannot be checked.** The endpoint's usage payload **does not report `reasoning_tokens`**, so "high" is only a request label — the run actually used the endpoint's default thinking budget. No same-band comparison is offered against other repos; the band column is honestly marked "requested, unverifiable".
2. **Vision face: endpoint incident.** Before launch, vision requests hung on this endpoint with zero bytes (a different model on the same endpoint answered the same image correctly in 6.8s). That case was first recorded `not run` (not a failure); after the endpoint recovered it was re-taken and the real value recorded. Both the incident and the makeup are written into Findings.
3. **Extended wall-clock caps.** The three verify cases only settled after the runner's time caps were doubled (7200/10800/3600 s), so the whole-issue wall clock runs heavy — carry this caveat when comparing wall time across repos.

## W41 in one minute

stepfun plan endpoint, high requested (**burn not verifiable**), isolated room, the same 24 cases (the prompt of the brand case A-d9b79b46 was changed on 10-07, so its re-sit paper has a new hash; the others have the same hashes): **step-5-preview 18'/24** (18 wins · 2 losses · 4 NA). The three cells that the W38 correction showed as "held, re-sit pending" were re-taken: A-1fd3683a passed (2/2); A-ea80d793 (vision) stays recorded as a loss; A-cdc3d11a (review) was also recorded as a loss at the time and, since 2026-10-07, is NA (held) on every lane because of the grader, not because of how the model answered (see the update above); on both the model answered with one sentence about what it would do first (on A-cdc3d11a with tool calls written out as text), the turn ended, and no answer was given. The 4 NA cells: A-d511f9e8 is NA on every lane (see the correction notice); A-cdc3d11a is held on every lane (see above); A-a317e74b and A-be92627f hit the time cap on both tries. The brand case A-d9b79b46 (UI): in the first paper on 10-06 the model wrote a tool call out as text and handed in no files, the text and the room did not match, and it was recorded NA following the 10-02 precedent; after the prompt change and the move to a neutral working directory on 10-07, only this cell was re-taken, the model gave in both files, 12/12, recorded as a pass; the same case on other lanes still stands on the old prompt, except claude-fable-5-1, which was re-sat once on 2026-10-07 under the changed prompt (loss, 11/12; see the [amber-claude W40 page](https://github.com/getaskclaw/amber-claude/blob/main/results/2026-W40.en.md)); the four WorkBuddy direct lanes' cells for this case have not been re-sat. The case-by-case matrix, the exam conditions and the notes on each NA are in the [2026-W41 issue](results/2026-W41.en.md).

Disclosure 1 in "Lane notes" above (burn not verifiable) applies to W41 as well; disclosures 2 and 3 are the endpoint incident and the extended caps of W38; there was no raised-cap re-run in W41, and timeouts are recorded NA.

## W38 base + W39 make-up

![W38 full-test base: step-5-preview 15/23; W39 make-up shown separately](docs/images/w38-face-profile-correction.en.png?v=corrections-20260924-r2)

stepfun plan endpoint, requested high band (**reasoning burn unverifiable**), same 23 cases same hashes: **step-5-preview 15/23** (13/21 on the public 21-case subset) — **build side top-tier**: ops 6/6 clean + req-drift all four variants + coding 5/6 (including the library's only hard discriminator A-442d4aab at a perfect 7/7) + delivery perfect; **judgement side trails**: the attribution axis beats the reference anchor k3 (0.800 vs 0.667 — the same case 12/15 vs 10/15), but verify 0/3, review net −2, vision −2, ui-build void. Three disclosures ride with the row: (1) the endpoint does not report `reasoning_tokens`, so the row is the endpoint's default band; (2) the vision face hung on this endpoint at launch with zero bytes (a different model on the same endpoint answered the same image fine), so that case was first `not run` and re-taken after recovery; (3) the three verify cases settled only under doubled wall-clock caps. Per-case matrix and lane ledger in the [W38 base / W39 make-up correction](results/2026-W38-correction-20260923.en.md) (original report kept at its old URL). Spec sources sit beside the PNGs (`docs/images/`, Vega-Lite).

## Publication rules (red lines)

1. Publish only: scores and totals, token usage, speed, verdicts.
2. Never publish: case content, oracles/graders, transcripts, candidate workspaces, any intermediate artifact that can rebuild a case, endpoint credentials.
3. Every issue pins: model id, effort band (the thinking-effort setting), date (UTC), harness version, per-case content hash (bundle_sha (per-case content-hash fingerprint)). The hashes are checkable against [amber](https://github.com/getaskclaw/amber)'s public hash index, self-proving the library did not change.
4. Case numbers and case structure are private: public results reference cases only by stable alias (A-xxxxxxxx, hash-derived) plus bundle hash. Internal case ids, variant names and case descriptions never appear.
5. Tone: this is measurement of a public endpoint, not an attack on any vendor. Let the data speak; keep the wording simple.

## One methods caveat

The same model on the same endpoint can score differently across runs — inference parameters, load and server version all drift. Every conclusion here carries its date and band. A single-day number is a snapshot, not a law.

## Results index

| Issue | Content | Verdict |
|---|---|---|
| [2026-W41](results/2026-W41.en.md) | step-5-preview, second full-library sitting on 2026-10-06 (isolated room, 24 cases; brand case re-taken 10-07) | **18'/24** (18 wins · 2 losses · 4 NA); A-1fd3683a, held in W38, passes; A-ea80d793 stays a loss; A-cdc3d11a is NA on every lane since 10-07 (grader); brand case A-d9b79b46 passes in a 10-07 re-sit after its prompt was changed; defense and attribution are all NA. Not compared cell by cell with the W38 sitting |
| [2026-W38 base](results/2026-W38-correction-20260923.en.md) | step-5-preview, full test on 2026-09-20 | Base 15/23; W39 convergence make-up adds 1 pass, giving 16'/24. The endpoint does not report actual thinking use. [Old report](results/2026-W39.md) |
| [Earlier full-library review](results/2026-W38-correction.en.md) | Historical notice: 0 cells reversed, 4 held | Its W39 label refers to the old report name. The full test was in W38; the held marks are not cleared here. |

## Disclaimer

Not affiliated with or sponsored by the StepFun team. Scores are snapshots under a particular date and load, and are not buying advice.