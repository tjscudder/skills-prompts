# Prompt Architect

Prompt Architect is a 9-step interactive wizard for designing optimized, production-ready prompts.
This README is aligned with the current local files:

- `prompt-architect.md` (source markdown)
- `prompt-architect.skill` (skill package/copy)

## Overview

The wizard guides users through:

1. Use-case, goal, and expedite mode
2. Task definition and classification
3. Inputs and context
4. Constraints and guardrails
5. Output format and target LLM selection
6. Few-shot examples
7. Voice (role/style, optional)
8. Quality checks and failure modes
9. Final assembly and review

At each step it follows: ask -> rewrite -> reflect -> confirm.

## Key Behavior

- Strict step-by-step flow with explicit approval before advancing
- Two pace modes:
  - `Expedite: full` (AI drafts all responses)
  - `Expedite: assisted` (AI suggests as needed)
- Inline command support:
  - `Suggest all`
  - `Suggest 1, 3`
  - `Approve`
  - `Revise 2: [feedback]`
  - Mixed input like `1. [answer]. 2. Suggest`
- Optional handoff intake from `solution-architect` via `HANDOFF_CONTEXT`

## Output Formats

The wizard can produce prompts in:

- XML
- JSON
- YAML
- Markdown
- Plain Text
- Skill (`.skill`)

Important `.skill` rules from the source:

- `.skill` is user-selectable only (never auto-recommended)
- `.skill` targets Claude-compatible usage
- Skill structure adapts by complexity (simple/moderate/complex)

## Files In This Folder

```text
prompt-architect/
├── README.md
├── prompt-architect.md
└── prompt-architect.skill
```

## Installation / Use

1. Upload `prompt-architect.skill` where your Claude skills are managed (global or project scope).
2. Trigger with phrases such as:
   - `/createprompt`
   - `/create-prompt`
   - "help me create a prompt"
   - "build a prompt for ..."
   - "design a system prompt"
   - "improve this prompt"
3. Complete the 9-step flow and approve each step.

## Editing and Sync Notes

- `prompt-architect.md` is the canonical editable source in this folder.
- `prompt-architect.skill` should be kept in sync with the source content when updates are made.
- If you change the workflow in `prompt-architect.md`, update this README to match behavioral and file-structure changes.
