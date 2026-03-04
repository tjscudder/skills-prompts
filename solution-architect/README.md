# Solution Architect

Solution Architect is a 4-phase interactive problem-solving system that moves from a vague challenge to a concrete deliverable.
This README is aligned with the current local files:

- `solution-architect.md` (source markdown)
- `solution-architect.skill` (skill package/copy)

## Overview

The skill guides users through:

1. Surface the real problem and desired outcome
2. Diagnose root causes with structured analysis
3. Design solutions and select the right delivery mode
4. Deliver the final artifact in the best format for execution

At each phase it follows: ask -> rewrite -> reflect -> confirm.

## Key Behavior

- Strict phase progression with explicit approval before advancing
- Two pace modes:
  - `Expedite: full` (AI drafts all responses)
  - `Expedite: assisted` (AI suggests on demand)
- Inline command support:
  - `Suggest all`
  - `Suggest 1, 3`
  - `Approve`
  - `Revise 2: [feedback]`
  - Mixed input like `1. [answer]. 2. Suggest`
- Continuous `CONTEXT_ACCUMULATED` tracking across phases
- Root-cause-first flow: no solutioning before diagnosis
- Honest deliverability classification:
  - `LLM-deliverable`
  - `LLM-assistable`
  - `Human-required`
- Cross-skill handoffs via `HANDOFF_CONTEXT` to:
  - `prompt-architect`
  - `deep-dive`

## Delivery Modes

Phase 3 recommends one or more output modes based on the diagnosed problem:

- Action Plan
- Decision Brief
- Claude Project Configuration
- Prompt Design (handoff)
- Strategy Document
- Learning Deep-Dive (handoff)
- Custom

## Files In This Folder

```text
solution-architect/
├── README.md
├── solution-architect.md
└── solution-architect.skill
```

## Installation / Use

1. Upload `solution-architect.skill` where your Claude skills are managed (global or project scope).
2. Trigger with phrases such as:
   - `/solution-architect`
   - `/solutionarchitect`
   - `/problem-solver`
   - "solution architect"
   - "help me think through this"
   - "I'm stuck with [problem]"
   - "help me set up a new project"
3. Complete the phase flow and approve each phase output.

## Editing and Sync Notes

- `solution-architect.md` is the canonical editable source in this folder.
- `solution-architect.skill` should be kept in sync with the source content when updates are made.
- If you change workflows, phase outputs, handoff protocol, or delivery modes in `solution-architect.md`, update this README to match.
