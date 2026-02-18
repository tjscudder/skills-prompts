# Skills & Prompts

A collection of interactive Claude skills, prompt configurations, and shared frameworks for LLM-powered workflows.

## Contents

| Folder | Type | Description |
|--------|------|-------------|
| [prompt-architect](./prompt-architect/) | Interactive Skill | 9-step wizard for creating optimized, production-ready LLM prompts. Interviews you about goals, constraints, and target LLM, then assembles a research-validated prompt. Includes a Universal Edition for non-Claude LLMs. |
| [project-architect](./project-architect/) | Interactive Skill | 4-step wizard for creating or refining Claude Project configurations. Produces Title, Description, Instructions, Knowledge Base recommendations, and Starter Templates. |
| [problem-architect](./problem-architect/) | Interactive Skill | 5-phase structured problem-solving system. Takes a vague problem through Surface, Diagnose, Decompose, Solve, and Plan & Execute phases using research-backed methodologies (JTBD, 5 Whys, MECE, Constraint Theory). Produces an actionable plan and offers to execute AI-deliverable parts. |
| [deep-dive](./deep-dive/) | Interactive Skill | Progressive topic learning system that takes you from zero to expert understanding through 4 structured phases: Orientation, Mechanics, Application, and Expert Territory. |
| [prompt-process](./prompt-process/) | Framework | Reusable step-oriented workflow framework extracted from Prompt Architect. Blueprint for building new multi-step interactive skills with expedite modes, context accumulation, and approval gates. |

> **Note:** The Master Prompt (personal LLM system prompt configuration) is maintained in a [separate private repository](https://github.com/tjscudder/master-prompt).

## Skill Commands

| Skill | Command | Description |
|-------|---------|-------------|
| Prompt Architect | `/createprompt` | Start the 9-step prompt creation wizard |
| Project Architect | `/project-architect` | Start the project configuration wizard |
| Problem Architect | `/problem-architect` | Start the structured problem-solving system |
| Deep Dive | `/deep-dive` | Start progressive learning on any topic |

## Installation

### Skills (.skill files)

1. Open [Claude.ai](https://claude.ai)
2. Navigate to your Project (or create one)
3. In Project Knowledge, click "Add content"
4. Upload the `.skill` file from the skill's folder
5. Start a new conversation and use the skill's command

### Deep Dive (SKILL.md)

1. Open [Claude.ai](https://claude.ai)
2. Navigate to your Project
3. Upload `deep-dive/SKILL.md` to Project Knowledge

See each folder's README for detailed installation options including global installation and manual setup.
