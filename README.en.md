# amber-stepfun

Weekly AMBER measurement of StepFun's new flagship `step-5-preview` as served on the **stepfun plan endpoint**. Results are public; cases never are.
中文: [README.md](README.md)

## What this is

- Every issue `results/YYYY-Www.md`: same cases, same harness, full-library run (23 cases / 26 papers).
- A fixed report shape: library size + hashes, per-case pass/fail, terminal states, token usage and wall clock, environment fingerprint, and qualitative verdicts written to evidence discipline.
- Cases, oracles, transcripts and intermediate artifacts are **never published** (see "Publishing rules" below).
- Sister repos: [amber-gpt](https://github.com/getaskclaw/amber-gpt), [amber-crof](https://github.com/getaskclaw/amber-crof), [amber-ollama](https://github.com/getaskclaw/amber-ollama), [amber-devin](https://github.com/getaskclaw/amber-devin), [amber-deepseek](https://github.com/getaskclaw/amber-deepseek), [amber-commandcode](https://github.com/getaskclaw/amber-commandcode), [amber-opencode](https://github.com/getaskclaw/amber-opencode), [amber-workbuddy](https://github.com/getaskclaw/amber-workbuddy), [amber-kimi](https://github.com/getaskclaw/amber-kimi), [amber-doubao](https://github.com/getaskclaw/amber-doubao), [amber-goldenpotato](https://github.com/getaskclaw/amber-goldenpotato).
- AMBER is an agentic real-world task library (build / ops / review / vision / requirement-drift). The spec and case-forging tooling live in [getaskclaw/amber](https://github.com/getaskclaw/amber); the cases themselves are private.

## Lane notes (what is special about this repo)

This repo measures StepFun's official **plan endpoint** (OpenAI-compatible) serving the new flagship `step-5-preview` (600B/27B MoE; the vendor advertises 1M context + vision).

Three extra disclosures therefore ride with the scores:

1. **Reasoning burn is unverifiable.** The endpoint's usage payload **does not report `reasoning_tokens`**, so "high" is only a request label — the run actually used the endpoint's default thinking budget. No same-band comparison is offered against other repos; the band column is honestly marked "requested, unverifiable".
2. **Vision face: endpoint incident.** Before launch, vision requests hung on this endpoint with zero bytes (a different model on the same endpoint answered the same image correctly in 6.8s). That case was first recorded `not run` (not a failure); after the endpoint recovered it was re-taken and the real value recorded. Both the incident and the makeup are written into Findings.
3. **Extended wall-clock caps.** The three verify cases only settled after the runner's time caps were doubled, so the whole-issue wall clock runs heavy — carry this caveat when comparing wall time across repos.

## W39 in one minute

![W39 debut profile: step-5-preview 15/23, build-side solid, judgement faces behind](docs/images/w39-face-profile.en.png?v=20260921)

stepfun plan endpoint, requested high band (**reasoning burn unverifiable**), same 23 cases same hashes: **step-5-preview 15/23** (13/21 on the public 21-case subset) — **build side top-tier**: ops 6/6 clean + req-drift all four variants + coding 5/6 (including the library's only hard discriminator A-442d4aab at a perfect 7/7) + delivery perfect; **judgement side trails**: the attribution axis beats the reference anchor k3 (0.800 vs 0.667 — the same case 12/15 vs 10/15), but verify 0/3, review net −2, vision −2, ui-build void. Three disclosures ride with the row: (1) the endpoint does not report `reasoning_tokens`, so the row is the endpoint's default band; (2) the vision face hung on this endpoint at launch with zero bytes (a different model on the same endpoint answered the same image fine), so that case was first `not run` and re-taken after recovery; (3) the three verify cases converged only under doubled wall-clock caps. Per-case matrix and lane ledger in the [2026-W39 issue](results/2026-W39.md). Spec sources sit beside the PNGs (`docs/images/`, Vega-Lite).

## Publication discipline (red lines)

1. Publish only: scores and aggregates, token usage, speed, qualitative verdicts.
2. Never publish: case content, oracles/scorers, transcripts, candidate workspaces, any intermediate artifact that can reconstruct a case, endpoint credentials.
3. Every issue pins: model id, effort band, date (UTC), harness version, per-case content hash (bundle_sha). The hashes are checkable against [amber](https://github.com/getaskclaw/amber)'s public hash index, self-proving the library did not change.
4. Case numbers and case structure are private: public results reference cases only by stable alias (A-xxxxxxxx, hash-derived) plus bundle hash. Internal case ids, variant names and case descriptions never appear.
5. Tone: this is measurement of a public endpoint, not an attack on any vendor. Let the data speak; keep the wording restrained.

## One methodological caveat

The same model on the same endpoint can score differently across runs — inference parameters, load and server version all drift. Every conclusion here therefore carries its date and band. A single-day number is a snapshot, not a law.

## Results index

| Issue | Content | Verdict |
|---|---|---|
| [2026-W39](results/2026-W39.md) | step-5-preview @ stepfun plan endpoint, full-library debut | case-level 15/23; ops 6/6, req-drift all variants, coding 5/6 (hard discriminator perfect), delivery perfect; attribution axis beats the anchor; review half, verify 0/3, vision −2, ui-build void; endpoint reports no reasoning burn |

## Disclaimer

No affiliation with or sponsorship from the StepFun team. Scores are snapshots under a particular date and load, and constitute no purchasing advice.
