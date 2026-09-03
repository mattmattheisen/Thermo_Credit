---
name: treasury-market-stress
description: Use when analyzing Treasury market functioning, bond-market stress or dysfunction, MOVE, repo or SOFR, Treasury auctions, settlement fails, dealer intermediation, or claims that the Treasury market is breaking.
---

# Treasury Market Stress

## Objective

Translate market commentary into a falsifiable question:

> Do current observable Treasury-market mechanics indicate NORMAL conditions, REPRICING, STRESS, or DYSFUNCTION?

The goal is not to predict yields or validate a headline. The goal is to determine whether market plumbing is actually deteriorating.

## Procedure

### 1. Establish the evidence set

For every candidate series record:
- authoritative source;
- series or field identifier;
- frequency;
- observation date;
- publication/release lag;
- available history;
- revision behavior;
- stress direction;
- known limitations.

Prefer primary/public sources such as the Federal Reserve, FRED, Federal Reserve Bank of New York, U.S. Treasury, and FINRA where appropriate.

Never invent a series, field, historical observation, or API behavior.

### 2. Protect point-in-time integrity

When a historical classification depends on what was knowable at the time:
- preserve observation and release dates where available;
- do not silently use future or revised information;
- label unavoidable retrospective inputs;
- preserve/cache raw source data where practical.

### 3. Keep price separate from function

Treat these as distinct:
1. price/yield level;
2. volatility/repricing speed;
3. market function.

A high or rapidly rising Treasury yield is context, not evidence by itself that the market is failing.

### 4. Score six independent pillars

Evaluate:
1. volatility;
2. liquidity;
3. funding;
4. auctions;
5. settlement;
6. intermediation.

Do not infer normality merely because a difficult-to-obtain pillar lacks good data. Surface the gap.

### 5. Normalize transparently

Start with:
- historical percentiles;
- robust z-scores;
- explicitly documented rolling distributions.

For every transformation document:
- lookback window;
- minimum history;
- winsorization, if any;
- missing-data behavior;
- stress direction.

Do not introduce HMMs, random forests, neural networks, or other ML until the transparent baseline has been historically validated.

### 6. Require breadth and persistence

Do not escalate the entire system because one series spikes.

Test:
- how many independent pillars confirm;
- severity within each pillar;
- persistence across observations;
- whether apparently independent signals are mechanically related;
- whether one indicator dominates the aggregate result.

### 7. Classify conservatively

**NORMAL**  
Market mechanics are broadly ordinary.

**REPRICING**  
Price/yield and possibly volatility are unusual, but core mechanics remain broadly functional.

**STRESS**  
Multiple independent market-function mechanisms show material deterioration.

**DYSFUNCTION**  
Severe, historically unusual impairment appears across multiple core mechanisms, or a critical mechanism shows severe persistent failure.

If evidence is insufficient, report uncertainty instead of forcing a state.

Do not create a CATASTROPHIC state. Catastrophe is a consequence or interpretation, not a directly measured market condition.

### 8. Validate against history

Use episodes for different diagnostic purposes rather than assuming all are examples of Treasury dysfunction.

Core dysfunction benchmark:
- March 2020 Treasury-market dysfunction.

Funding/intermediation stress benchmark:
- September 2019 repo disruption.

Boundary/diagnostic episodes:
- 2008 financial crisis;
- 2011 U.S. debt-ceiling episode;
- 2023 regional-bank stress.

Negative controls should include large or frightening bond moves that remained broadly functional, for example:
- 1994 bond-market selloff;
- 2013 taper tantrum;
- 2022 rapid Fed-tightening/Treasury selloff.

The framework must distinguish scary price action from impaired mechanics.

### 9. Run falsification and ablation tests

At minimum test:
- exclude MOVE;
- exclude yield-change variables;
- leave one pillar out;
- alternative reasonable lookbacks;
- alternative persistence requirements;
- threshold sensitivity;
- missing-data effects;
- component concentration.

Ask explicitly:

> Can this framework distinguish March 2020 from an ordinary bond selloff?

If not, improve measurement before increasing model complexity.

### 10. Keep classification separate from investment advice

Separate:
- observation;
- calculation;
- inference;
- hypothesis;
- investment implication.

Do not convert a market-state classification into a duration, curve, or trading recommendation without a separately specified and validated decision rule.

## Required Report

Return an auditable instrument panel containing:

```text
TREASURY MARKET STATUS
As of: YYYY-MM-DD

Yield Environment: ...
Volatility: ...
Liquidity: ...
Funding: ...
Auctions: ...
Settlement: ...
Intermediation: ...

Market Function Score: XX/100  [only if justified]
Classification: NORMAL | REPRICING | STRESS | DYSFUNCTION
Evidence of systemic dysfunction: YES | NO | UNCERTAIN

Primary drivers:
- ...

Evidence against the classification:
- ...

Data warnings:
- ...

- ...
```

Also expose:
- data freshness;
- missing/stale inputs;
- current raw observations;
- normalized historical context;
- pillar scores/states;
- historical analogues;
- limitations;
- concise plain-English interpretation.

## Completion Check

Before finalizing, confirm that:
- the conclusion was not assumed in advance;
- price, volatility, and market function were kept distinct;
- weak or missing data were surfaced;
- the state requires breadth/persistence rather than one dramatic series;
- at least one negative control is part of validation;
- null findings and counterevidence are reported;
- the result is reproducible from documented inputs and rules.
