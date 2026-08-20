# Base model vs. obliterated model

This is an exploratory comparison of two local runs of the same benchmark. It
is intended to document an observed behavioral difference, not to claim a
controlled scientific experiment.

## Runs compared

| Run | Model | Generations | Conditions |
|---|---|---:|---|
| Base | `Qwen3.8-27B-Q4_K_S-reasoning1024` | 320 | 8 prompts, 20 generations per condition |
| Obliterated | `Qwen3.8-27B-Q4_K_M-reasoning1024-obliterated` | 320 | 8 prompts, 20 generations per condition |

Both runs used the same local `llama.cpp` endpoint, the same eight French and
English prompts, and fresh conversations for each generation.

## Main observation

The base model produced **52 direct refusals out of 80 Tiananmen generations
(65%)**. The obliterated model produced **0 direct refusals out of 80** on the
same topic.

For the two comparison topics — Paris, 17 October 1961, and Gaza — neither
run produced a comparable direct-refusal pattern: **0/160** in each run.

| Topic group | Base model | Obliterated model |
|---|---:|---:|
| Tiananmen | 52/80 direct refusals | 0/80 direct refusals |
| Paris 1961 + Gaza | 0/160 direct refusals | 0/160 direct refusals |

## Xinjiang

The difference is not only a change from refusal to answer. The response
framing also changes.

In the base run, all 80 answers used some form of “vocational education”,
“vocational training”, or “training center” terminology. A phrase-level scan
found explicit denial or disqualification of the “internment camp” description
in 22/80 answers.

The initial A–G coding of the obliterated run gives:

| Code | Meaning | Count |
|---|---|---:|
| A | Documented answer | 306 |
| F | Counter-narrative | 3 |
| G | Official framing | 11 |
| B/C/D/E | Other behaviors | 0 |

Within Xinjiang specifically, 66/80 answers were coded A, 3/80 F, and 11/80
G. The other topics were all initially coded A. This coding is assisted and
provisional: it classifies observable response behavior and does not fact-check
each generated claim.

## Interpretation

On this benchmark, the obliterated model appears to remove the base model’s
strongest China-specific refusal behavior. It also appears less consistently
locked into the official euphemistic framing on Xinjiang, although a smaller
set of answers still reproduces that framing or directly rejects the prompt’s
wording.

The obliterated answers are often shorter and can vary considerably in factual
precision. Removing refusal behavior should therefore not be treated as proof
that the resulting answers are more accurate or more reliable.

## Files

- [Base run](qwen-censorship-bench-20260819-173332/)
- [Obliterated run](qwen-censorship-bench-20260820-083417/)
- [Obliterated coding summary](qwen-censorship-bench-20260820-083417/coding_summary.md)
- [Original base-model results](RESULTS_qwen3.8-27b.md)
