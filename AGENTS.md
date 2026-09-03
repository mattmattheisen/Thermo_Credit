# AGENTS.md — Thermo Credit

## Purpose

This repository is an evidence-first research and decision system built around credit creation and market conditions.

The immediate extension is a **Treasury Market Stress Monitor** designed to answer:

> Is the Treasury/bond market undergoing ordinary repricing, genuine stress, or measurable dysfunction?

The objective is not to prove financial-media headlines wrong, predict interest rates, or manufacture a trading signal.

## Prime Directive

Separate three different phenomena:

1. **Price** — bond prices and yield levels.
2. **Volatility** — speed and magnitude of repricing.
3. **Market function** — whether liquidity, funding, auctions, settlement, and intermediation continue to work.

A high or rapidly rising Treasury yield is not, by itself, evidence of Treasury-market failure.

## Research Neutrality

Do not begin with the conclusion that current bond-market commentary is exaggerated.

The hypothesis is genuinely two-sided:

- H0: observed conditions are consistent with functioning markets undergoing repricing.
- H1: observable market-function measures show meaningful stress or dysfunction.

If the evidence supports dysfunction, report dysfunction.
If it supports repricing, report repricing.
If evidence is mixed or incomplete, report uncertainty.

Never tune a model to reach a preferred narrative.

## Repository Workflow for ChatGPT/Codex

Before making material changes:

1. Inspect the repository structure.
2. Read existing README/docs/configuration.
3. Identify existing data sources, calculations, outputs, tests, and conventions.
4. Map the existing Richard Werner / credit-creation implementation.
5. Identify reusable code before proposing new modules.
6. Explain the smallest coherent implementation plan.
7. Only then modify code.

When implementing:

- Make incremental changes.
- Preserve existing behavior unless change is explicitly required.
- Run relevant existing tests before and after modifications.
- Add tests for new scoring/state behavior.
- Never invent an API, field, series, historical observation, or source.
- Surface missing/stale data rather than silently replacing it.
- Keep raw data, transformations, scoring, validation, and presentation separable.
- Prefer configuration over hard-coded thresholds.
- Document material assumptions.

## Existing Thermo Credit / Werner Layer

Preserve the repo's existing Richard Werner-inspired framework.

Conceptually, this layer may examine:
- bank credit creation;
- changes in credit;
- destination of credit;
- productive versus asset-oriented credit;
- credit expansion/contraction;
- relationships to economic activity and asset prices.

Do not rewrite or reinterpret the existing framework until the actual repository implementation has been inspected.

## Treasury Market Stress Layer

Treat this as a distinct analytical layer unless an empirical relationship with the Werner layer is demonstrated.

### Pillar 1 — Volatility

Candidate measures:
- MOVE;
- rolling changes in 2Y, 5Y, 10Y, 30Y Treasury yields;
- realized Treasury volatility.

### Pillar 2 — Liquidity

Candidate measures:
- bid/ask spreads;
- market depth;
- price-impact/liquidity proxies;
- other defensible public Treasury-liquidity measures.

Do not infer “normal liquidity” merely because high-quality liquidity data are unavailable.

### Pillar 3 — Funding

Candidate measures:
- SOFR;
- repo dislocations;
- spreads to relevant policy/funding benchmarks;
- funding dispersion or other documented pressure measures.

### Pillar 4 — Auctions

Candidate measures:
- bid-to-cover;
- tail / stop-through;
- indirect bidder share;
- primary dealer takedown.

One weak auction does not establish systemic dysfunction. Test breadth and persistence.

### Pillar 5 — Settlement

Candidate measures:
- Treasury fails-to-deliver;
- magnitude relative to history;
- persistence.

### Pillar 6 — Intermediation

Candidate measures:
- primary dealer Treasury positions/inventories;
- unusual dealer absorption of issuance;
- defensible dealer-balance-sheet/intermediation proxies.

## State Taxonomy

Use four interpretable states:

### NORMAL
No material evidence of impaired market function.

### REPRICING
Yields and/or volatility may be elevated, but market plumbing remains broadly functional.

### STRESS
Multiple independent market-function measures show material deterioration.

### DYSFUNCTION
Historically extreme impairment is visible across multiple core mechanisms, or a critical mechanism shows severe persistent failure.

Do not create a “CATASTROPHIC” state. Catastrophe is a consequence/interpretation, not a directly measured market state.

## V1 Method

Start simple.

Prefer:
- historical percentiles;
- robust z-scores;
- explicitly documented rolling distributions;
- transparent pillar aggregation;
- breadth and persistence requirements.

For each indicator:
1. identify source;
2. record release/publication lag;
3. determine stress direction;
4. define historical comparison window;
5. normalize;
6. calculate indicator state;
7. aggregate into pillar state;
8. aggregate pillars into market state.

Do not introduce HMMs, random forests, neural networks, or other ML until a transparent baseline has been historically validated.

## Point-in-Time Integrity

Whenever a historical claim depends on what could have been known at the time:

- preserve observation date and release date where available;
- do not silently use revised data;
- document unavoidable limitations;
- do not leak future information into historical classifications.

Maintain immutable/cacheable raw inputs where practical.

## Historical Validation

At minimum investigate:

- 2008 financial crisis;
- 2011 U.S. debt-ceiling episode;
- September 2019 repo disruption;
- March 2020 Treasury-market dysfunction;
- 2023 regional-bank stress.

Also include **negative controls**:
- substantial Treasury yield increases;
- high-rate environments;
- volatility episodes;
- ordinary bond selloffs that did not become Treasury-market dysfunction.

The system must demonstrate that it can distinguish scary price action from impaired mechanics.

## Falsification

Actively try to break the model.

Test:
- removal of MOVE;
- removal of yield-change variables;
- leave-one-pillar-out classifications;
- alternative reasonable lookbacks;
- persistence requirements;
- sensitivity to thresholds;
- dominance by a single series;
- missing-data effects.

Ask:

> Can this framework distinguish March 2020 from an ordinary bond selloff?

If not, improve the measurement framework before increasing model complexity.

## Output Contract

The preferred output is an auditable instrument panel:

```text
TREASURY MARKET STATUS
As of: YYYY-MM-DD

Yield Environment: Elevated
Volatility: Elevated
Liquidity: Normal
Funding: Normal
Auctions: Normal
Settlement: Normal
Intermediation: Normal

Market Function Score: XX/100
Classification: REPRICING
Evidence of systemic dysfunction: NO

Primary drivers:
- ...
- ...

Evidence against the classification:
- ...

Data warnings:
- ...
```

Every report should expose:
- as-of date;
- data freshness;
- missing/stale inputs;
- raw/current observations;
- normalized historical context;
- pillar scores/states;
- aggregate classification;
- principal drivers;
- counterevidence;
- concise plain-English interpretation.

Avoid false precision.

## Decision Boundary

A market-state classification is not automatically an investment recommendation.

Do not infer from the monitor alone:
- buy bonds;
- sell bonds;
- extend duration;
- shorten duration;
- recession;
- equity decline;
- Fed action.

Each requires a separate hypothesis and test.

Always ask:

> What decision does this information allow us to make that we could not make before?

If the answer is none, label the result descriptive.

## Werner + Treasury Integration

Do not assume credit creation causes, predicts, or confirms Treasury stress.

Possible later hypotheses may test whether:
- bank-credit contraction precedes/amplifies Treasury stress;
- credit destination matters;
- the Werner layer adds classification or decision value.

These relationships must be tested independently.

## Headline-vs-Reality Module

This is a later phase, not a V1 dependency.

Only after the market-function methodology is frozen:

1. define headline terms in advance;
2. gather timestamped historical headlines;
3. construct a reproducible headline-intensity measure;
4. compare headline intensity with independent market-function states;
5. quantify false alarms and correspondence with real stress.

Possible terms:
- bond rout;
- bond crisis;
- Treasury turmoil;
- bond market breaking;
- bond market failure.

Never use the headlines being tested to define the ground-truth market state.

## Coding Standards

- Python-first unless the existing repo strongly indicates otherwise.
- Follow existing repo conventions.
- Small, testable modules.
- Separate ingestion, normalization, scoring, validation, and reporting.
- Type hints where consistent with the codebase.
- Clear docstrings for non-obvious research logic.
- Configuration for series IDs, lookbacks, and thresholds where practical.
- Tests for boundary conditions and state transitions.
- Reproducibility over cleverness.

## Completion Standard

A task is not complete merely because code runs.

For research changes, report:
1. what changed;
2. what data were used;
3. what tests ran;
4. what passed/failed;
5. assumptions/limitations;
6. whether conclusions are descriptive or decision-useful;
7. what evidence could falsify the result.

Null findings are valid findings.
