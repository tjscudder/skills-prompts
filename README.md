# Skills & Prompts

A curated set of Claude skills for moving from unclear problems to concrete outcomes:

- diagnose and deliver solutions (`solution-architect`)
- design high-quality prompts (`prompt-architect`)
- learn topics deeply and progressively (`deep-dive`)

## Skills Included

| Folder | Type | Description |
| -------- | ------ | ----------- |
| [solution-architect](./solution-architect/) | Interactive Skill | 4-phase problem-to-deliverable system: Surface, Diagnose, Solve, Deliver. Uses structured methods (JTBD, adaptive 5 Whys, Ishikawa, MECE, Constraint Theory) and adapts output mode to need (Action Plan, Decision Brief, Claude Project config, Strategy Doc, Prompt handoff, Learning handoff, or Custom). |
| [prompt-architect](./prompt-architect/) | Interactive Skill | 9-step interactive prompt design wizard with approve/edit gates, expedite modes, context accumulation, LLM-specific format guidance, and final assembly in research-validated output order. Supports optional `.skill` output for reusable Claude skills. |
| [deep-dive](./deep-dive/) | Interactive Skill | Progressive 4-phase learning system (Orientation, Mechanics, Application, Expert Territory) with learner-controlled pacing, branching, comprehension checks, and practical summary/resources outputs. |

## Skill Commands

| Skill | Commands |
| ------- | ---------- |
| Solution Architect | `/solution-architect`, `/solutionarchitect`, `/problem-solver`, `/project-architect` |
| Prompt Architect | `/createprompt`, `/create-prompt` |
| Deep Dive | `/deep-dive`, `/deepdive` |

## How They Work Together

These skills are designed to compose through `HANDOFF_CONTEXT` blocks:

- `solution-architect` can hand off to `prompt-architect` when the solution requires prompt design.
- `solution-architect` can hand off to `deep-dive` when a knowledge gap is the blocker.
- `prompt-architect` and `deep-dive` can ingest handoff context to skip redundant discovery and start at the right step/phase.

## Shared Interaction Pattern

All three skills emphasize:

- structured, phase/step-based progression
- explicit user control (`APPROVE`/`EDIT`)
- optional expedite mode (`full` or `assisted`) where applicable
- context accumulation across phases for better output consistency

## Installation

Each folder includes a packaged `.skill` file:

- `deep-dive/deep-dive.skill`
- `prompt-architect/prompt-architect.skill`
- `solution-architect/solution-architect.skill`

To install in Claude:

1. Open [Claude.ai](https://claude.ai)
2. Open a Project (or create one)
3. In Project Knowledge, click **Add content**
4. Upload the desired `.skill` file
5. Start a new chat and invoke the skill command

For per-skill details, see each folder's `README.md`.
