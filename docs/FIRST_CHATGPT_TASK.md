# First ChatGPT/Codex Task

Use this after the Thermo Credit repository is available.

## Prompt

Inspect the entire Thermo Credit repository before changing any code.

Read `AGENTS.md`, the existing README/documentation, dependency/configuration files, tests, and `.agents/skills/treasury-market-stress/SKILL.md`.

Then produce a repository assessment covering:

1. Current architecture and execution flow.
2. Existing Richard Werner / credit-creation methodology as actually implemented.
3. Every current external data source/API and the fields/series being used.
4. Existing calculations, scoring, reports, charts, and outputs.
5. Existing test coverage.
6. Code or infrastructure that can be reused for a Treasury Market Stress Monitor.
7. For each proposed Treasury pillar — volatility, liquidity, funding, auctions, settlement, intermediation — identify:
   - data already present;
   - authoritative public data that can be added;
   - frequency and history;
   - publication lag/revisions;
   - point-in-time concerns;
   - data gaps.
8. Propose the smallest V1 architecture that can distinguish NORMAL, REPRICING, STRESS, and DYSFUNCTION using transparent rules.
9. Propose historical positive cases and negative controls.
10. Identify the biggest methodological risks before implementation.

Do not implement the monitor yet.

Do not assume current bond-market headlines are exaggerated or correct. The framework must be capable of returning either conclusion.

End with a proposed implementation sequence broken into small, testable commits.
