# bidradar

BidRadar's entire "codebase" lives here: runtime prompts, Make blueprints, Airtable schema, code snippets, and weekly state snapshots. In a no-code stack the code is in vendor dashboards — this repo is the recovery plan and the change history.

## Structure

```
bidradar/
├── prompts/            ← live version of each runtime prompt (Prompts A–E)
│   └── samples/        ← 3 saved sample inputs per prompt, for pre-commit testing
├── make-blueprints/    ← exported Make scenario JSON (⋯ menu → Export Blueprint)
├── airtable/
│   └── schema.md       ← tables + fields, updated whenever schema changes
├── code/               ← any custom snippets (webhook handlers, date math)
├── state-snapshots/    ← weekly BIDRADAR STATE blocks, one file per week
└── README.md
```

## Rules

- **Prompts are code.** Every prompt edit = a commit with a message saying what changed and why (e.g., "tightened scoring rule — too many 65-mile matches passing"). If a new prompt version degrades output, revert to the last commit.
- **Blueprints get re-exported and committed whenever a scenario changes.** This is the only way to recover a deleted or broken Make scenario.
- **Test before commit.** Run a changed prompt against the 3 sample inputs in `prompts/samples/` and compare outputs before it goes live in Make.
- **Friday ritual.** Export changed blueprints, commit the week's state snapshot.

## How to restore everything from this repo

1. **Airtable** — rebuild the base from `airtable/schema.md` (exact table and field names).
2. **Make** — create a new scenario → ⋯ menu → Import Blueprint → pick the JSON from `make-blueprints/`. Reconnect the Airtable, Claude API, and email connections (credentials aren't stored in blueprints).
3. **Prompts** — paste the current file from `prompts/` into the matching Claude API module in each Make scenario. Model: `claude-sonnet-5`. Temperatures: A 0.1, B 0.3, C 0.4, D 0.2.
4. **Post-Prompt-A filter** — only write to MATCHES when `match_score ≥ 70` AND `eligibility_flag ≠ "ineligible"`.
5. **State** — read the latest file in `state-snapshots/` to know where the business stands.
