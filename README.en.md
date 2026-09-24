# amber-stepfun

> Week correction: full test in W38; publication and convergence make-up in W39. The combined score stays 16'/24. [Correction](results/2026-W38-correction-20260923.en.md). Existing held-case notices remain in force.

' = contested (held for safety refusal) or invalid (infrastructure-related (test harness or scoring environment) cases: held, void or awaiting re-scoring); neither counts as a win or a loss. Every lane with NA carries an apostrophe, including frozen display rows; a hold does not settle the cause. StepFun: 4 held cells, not wins or losses.


Weekly AMBER measurement of StepFun's new flagship `step-5-preview` as served on the **stepfun plan endpoint**. Results are public; cases never are.
中文: [README.md](README.md)

## What this is

- A 'lane' is one vendor's shop/API for a model name; a 'case' is one task, a 'run' is one sitting (a multi-variant case has several runs).

- Every issue `results/YYYY-Www.md`: same cases, same harness (the program that runs the exam and scores it), full-library run (23 cases / 26 papers).
- A fixed report shape: library size + hashes, per-case pass/fail, terminal states (how the run process exited), token usage and wall clock, environment fingerprint, and qualitative verdicts written to evidence discipline.
- Cases, oracles, transcripts (full answer logs)s and intermediate artifacts are **never published** (see "Publishing rules" below).
- Sister repos: [amber-gpt](https://github.com/getaskclaw/amber-gpt), [amber-crof](https://github.com/getaskclaw/amber-crof), [amber-ollama](https://github.com/getaskclaw/amber-ollama), [amber-devin](https://github.com/getaskclaw/amber-devin), [amber-deepseek](https://github.com/getaskclaw/amber-deepseek), [amber-commandcode](https://github.com/getaskclaw/amber-commandcode), [amber-opencode](https://github.com/getaskclaw/amber-opencode), [amber-workbuddy](https://github.com/getaskclaw/amber-workbuddy), [amber-kimi](https://github.com/getaskclaw/amber-kimi), [amber-doubao](https://github.com/getaskclaw/amber-doubao), [amber-goldenpotato](https://github.com/getaskclaw/amber-goldenpotato).
- AMBER is an agentic real-world task library (build / ops / review / vision / requirement-drift (the requirements change mid-task)). The spec and case-forging tooling live in [getaskclaw/amber](https://github.com/getaskclaw/amber); the cases themselves are private.

## Lane notes (what is special about this repo)

This repo measures StepFun's official **plan endpoint** (OpenAI-compatible) serving the new flagship `step-5-preview` (600B/27B MoE; the vendor advertises 1M context + vision).

Three extra disclosures therefore ride with the scores:

1. **Reasoning burn is unverifiable.** The endpoint's usage payload **does not report `reasoning_tokens`**, so "high" is only a request label — the run actually used the endpoint's default thinking budget. No same-band comparison is offered against other repos; the band column is honestly marked "requested, unverifiable".
2. **Vision face: endpoint incident.** Before launch, vision requests hung on this endpoint with zero bytes (a different model on the same endpoint answered the same image correctly in 6.8s). That case was first recorded `not run` (not a failure); after the endpoint recovered it was re-taken and the real value recorded. Both the incident and the makeup are written into Findings.
3. **Extended wall-clock caps.** The three verify cases only settled after the runner's time caps were doubled, so the whole-issue wall clock runs heavy — carry this caveat when comparing wall time across repos.

## W38 base + W39 make-up

![W38 full-test base: step-5-preview 15/23; W39 make-up shown separately](docs/images/w38-face-profile-correction.en.png?v=corrections-20260924-r2)

stepfun plan endpoint, requested high band (**reasoning burn unverifiable**), same 23 cases same hashes: **step-5-preview 15/23** (13/21 on the public 21-case subset) — **build side top-tier**: ops 6/6 clean + req-drift all four variants + coding 5/6 (including the library's only hard discriminator A-442d4aab at a perfect 7/7) + delivery perfect; **judgement side trails**: the attribution axis beats the reference anchor k3 (0.800 vs 0.667 — the same case 12/15 vs 10/15), but verify 0/3, review net −2, vision −2, ui-build void. Three disclosures ride with the row: (1) the endpoint does not report `reasoning_tokens`, so the row is the endpoint's default band; (2) the vision face hung on this endpoint at launch with zero bytes (a different model on the same endpoint answered the same image fine), so that case was first `not run` and re-taken after recovery; (3) the three verify cases converged only under doubled wall-clock caps. Per-case matrix and lane ledger in the [W38 base / W39 make-up correction](results/2026-W38-correction-20260923.en.md) (original report kept at its old URL). Spec sources sit beside the PNGs (`docs/images/`, Vega-Lite).

## Publication discipline (red lines)

1. Publish only: scores and aggregates, token usage, speed, qualitative verdicts.
2. Never publish: case content, oracles/scorers, transcripts, candidate workspaces, any intermediate artifact that can reconstruct a case, endpoint credentials.
3. Every issue pins: model id, effort band (the thinking-effort setting), date (UTC), harness version, per-case content hash (bundle_sha (per-case content-hash fingerprint)). The hashes are checkable against [amber](https://github.com/getaskclaw/amber)'s public hash index, self-proving the library did not change.
4. Case numbers and case structure are private: public results reference cases only by stable alias (A-xxxxxxxx, hash-derived) plus bundle hash. Internal case ids, variant names and case descriptions never appear.
5. Tone: this is measurement of a public endpoint, not an attack on any vendor. Let the data speak; keep the wording restrained.

## One methodological caveat

The same model on the same endpoint can score differently across runs — inference parameters, load and server version all drift. Every conclusion here therefore carries its date and band. A single-day number is a snapshot, not a law.

## Results index

| Issue | Content | Verdict |
|---|---|---|
| [2026-W38 base](results/2026-W38-correction-20260923.en.md) | step-5-preview, full test on 2026-09-20 | Base 15/23; W39 convergence make-up adds 1 pass, giving 16'/24. The endpoint does not report actual thinking use. [Old report](results/2026-W39.md) |
| [Earlier full-library review](results/2026-W38-correction.en.md) | Historical notice: 0 cells reversed, 4 held | Its W39 label refers to the old report name. The full test was in W38; the held marks are not cleared here. |

## Disclaimer

No affiliation with or sponsorship from the StepFun team. Scores are snapshots under a particular date and load, and constitute no purchasing advice.
