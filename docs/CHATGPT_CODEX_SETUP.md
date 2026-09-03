# Thermo Credit — ChatGPT/Codex Project Kit

This kit is designed for the current OpenAI ChatGPT/Codex workflow.

## Drop these files into the repository

```text
Thermo-Credit/
├── AGENTS.md
├── .agents/
│   └── skills/
│       └── treasury-market-stress/
│           ├── SKILL.md
│           └── agents/
│               └── openai.yaml
├── docs/
│   └── FIRST_CHATGPT_TASK.md
└── CHATGPT_PROJECT_INSTRUCTIONS.md
```

## What each file does

- `AGENTS.md` is the durable repository-level instruction file Codex reads as project guidance.
- `.agents/skills/treasury-market-stress/SKILL.md` is the focused reusable Treasury-market research workflow.
- `.agents/skills/treasury-market-stress/agents/openai.yaml` supplies OpenAI-facing skill metadata.
- `docs/FIRST_CHATGPT_TASK.md` is the first work order: inspect and map the existing repo before implementation.
- `CHATGPT_PROJECT_INSTRUCTIONS.md` is a compact instruction set for a ChatGPT Project. Paste its contents into Project settings if you are also using the repo from ordinary ChatGPT project chats.

## Recommended first move

1. Add these files to your Thermo Credit fork.
2. Open the repository in Codex.
3. Start with the task in `docs/FIRST_CHATGPT_TASK.md`.
4. The first pass should make **no code changes**. It should map the current Werner/credit-creation implementation, data sources, tests, and reusable infrastructure.
5. Only after that assessment should the Treasury Market Stress Monitor V1 be designed and implemented.

## Research boundary

The Treasury layer is not designed to prove that financial-media commentary is exaggerated. It is designed to distinguish:

`NORMAL -> REPRICING -> STRESS -> DYSFUNCTION`

using observable market mechanics and historical falsification.

Keep the existing Richard Werner/credit-creation framework separate until an empirical relationship between the two layers is demonstrated.
