# Problem Architect Skill

> Structured Problem Solving System

## 1. Overview

Problem Architect is a structured problem-solving system that takes users from a vague, ill-defined problem to a clear, actionable plan through 5 research-backed phases. It's designed for situations where you don't fully understand the problem you're facing or where to start solving it.

The skill synthesizes established problem-solving methodologies including Jobs-to-be-Done, Root Cause Analysis (5 Whys), Ishikawa/Fishbone diagrams, MECE decomposition, Constraint Theory, First Principles Thinking, and Design Thinking into a guided conversational flow.

At the end, it produces a structured plan and offers to execute any parts the AI can deliver.

### Table of Contents

1. [Overview](#1-overview)
2. [What It Does](#2-what-it-does)
3. [What It Outputs](#3-what-it-outputs)
4. [Installation: Claude.AI](#4-installation-claudeai)
5. [Triggering the Skill](#5-triggering-the-skill)
6. [How to Use the Skill](#6-how-to-use-the-skill)
7. [Troubleshooting](#7-troubleshooting)
8. [File Structure](#8-file-structure)
9. [Version History](#9-version-history)
10. [Contact & Support](#10-contact--support)

---

## 2. What It Does

The skill guides you through five phases, each building clarity on the last:

1. **Phase 1 -- Surface** (Problem Discovery) - Extract the real problem from your vague description. Identifies the desired outcome, stakeholders, prior attempts, and synthesizes a clear problem statement.
2. **Phase 2 -- Diagnose** (Root Cause Analysis) - Move from symptoms to root causes using adaptive 5 Whys and Ishikawa dimension analysis. Produces a causal chain showing why the problem exists.
3. **Phase 3 -- Decompose** (Problem Structure) - Break the problem into a structured set of sub-problems using MECE decomposition. Each sub-problem is classified by whether the AI can deliver it, assist with it, or if it requires human action.
4. **Phase 4 -- Solve** (Solution Design) - Generate concrete solution approaches starting from the binding constraint. Validates the full solution set against your desired outcome.
5. **Phase 5 -- Plan & Execute** (Structured Plan + Execution) - Assembles a structured action plan and offers to execute AI-deliverable components on the spot.

### Core Principles

- **Extract before solving** -- The real problem is rarely the stated problem; invest in diagnosis
- **User controls direction** -- Never advance without your explicit approval
- **Progressive clarity** -- Each phase visibly reduces ambiguity
- **Action-oriented output** -- Every phase produces a concrete artifact, not just conversation
- **Honest about boundaries** -- Clearly distinguishes what the AI can deliver vs. what requires human action

### Research Foundation

| Framework | Phase | Purpose |
|-----------|-------|---------|
| Jobs-to-be-Done | Surface | Uncover the actual desired outcome |
| Socratic Method | Surface, Diagnose | Leading questions for self-discovery |
| 5 Whys | Diagnose | Iterative causal analysis |
| Ishikawa/Fishbone | Diagnose | Categorize causes across dimensions |
| First Principles | Diagnose, Decompose | Break down to fundamental truths |
| MECE Principle | Decompose | Exhaustive, non-overlapping decomposition |
| Constraint Theory | Decompose, Solve | Identify and solve the bottleneck first |
| Design Thinking | Solve | Generate multiple solution paths |

---

## 3. What It Outputs

### Per-Phase Outputs

Each phase produces a structured summary (e.g., `SURFACE_SUMMARY`, `DIAGNOSIS_SUMMARY`, `DECOMPOSITION_SUMMARY`, `SOLUTION_DESIGN`) that feeds into the next phase through context accumulation.

### Final Deliverables

**Structured Plan** including:
- Refined problem statement
- Root cause and causal chain
- Desired outcome
- Prioritized action plan table (sub-problem, approach, owner, deliverability, success criteria)
- Dependencies and sequencing
- Key assumptions and risks

**Execution Offer** categorized as:
- **LLM-deliverable** -- Items the AI can produce for you immediately (documents, plans, code, analysis, frameworks)
- **LLM-assistable** -- Items the AI can accelerate (templates, coaching, reviews, brainstorming)
- **Human-required** -- Items you need to handle yourself (with suggested approaches)

---

## 4. Installation: Claude.AI

### Option 1: Global Installation (All Chats)

To make the skill available across ALL your Claude conversations:

1. Open Claude.ai and click on your profile icon (bottom-left)
2. Select "Settings"
3. Navigate to the "Capabilities" section
4. Under Skills or Custom Instructions, click "Add" or "Upload"
5. Upload the `problem-architect.skill` file (Claude will extract and read the SKILL.md inside)
6. Save your settings
7. The skill is now available in ALL your conversations, not just projects

### Option 2: Project-Specific Installation

To use this skill only within a specific Project:

1. Open Claude.ai and navigate to your Project (or create a new one)
2. In the Project Knowledge section, click "Add content"
3. Select "Upload files" and choose the `problem-architect.skill` file (Claude will extract and read the SKILL.md inside)
4. The skill is now available in that Project's conversations only

### Option 3: Manual Installation (Copy/Paste)

If file upload isn't working, you can add the skill manually:

1. Unzip the .skill file (it's a ZIP archive -- rename to .zip if needed)
2. Open the extracted `problem-architect/SKILL.md` file
3. Copy the entire contents
4. Paste into either:
   - Settings > Capabilities (for global access), or
   - Project Knowledge (for project-specific access)

---

## 5. Triggering the Skill

Use one of these triggers in any conversation:

- `/problem-architect` or `/problemarchitect`
- "I have a problem"
- "I'm stuck on..."
- "Help me figure out..."
- "I don't know how to approach..."
- "What should I do about..."
- "How do I solve..."
- "I need a plan for..."
- "Help me think through..."
- "I'm not sure what the real issue is"

The skill will confirm the problem context and begin at Phase 1.

If you're already mid-conversation about a problem, the skill will infer context and confirm before starting.

---

## 6. How to Use the Skill

### Starting a Session

Describe your problem, however vaguely:

> "I'm stuck -- my team keeps missing deadlines and I don't know why"

The skill begins at Phase 1 (Surface) and guides you from there.

### Expedite Modes

Choose your preferred pace at the start:

- **Expedite: full** -- The AI drafts all responses; you review and approve
- **Expedite: assisted** -- The AI offers suggestions on request; you decide (default)

### Commands Available at Any Phase

| Command | Action |
|---------|--------|
| `Suggest all` | AI drafts responses for all questions |
| `Suggest 1, 3` | AI drafts specific questions |
| `Approve` | Accept suggestions as-is |
| `1. [response]` | Answer or edit question 1 |
| `1. [answer]. 2. Suggest` | Mix direct answers with AI suggestions |
| `Revise 2: [feedback]` | Ask AI to revise a specific suggestion |

### Navigating Between Phases

At the end of each phase, you'll see numbered options. Choose by number or describe what you want:

- **Proceed** to the next phase
- **Refine** the current phase's output
- **Branch** to explore a different angle
- **Skip ahead** to a later phase
- **Go deeper** on a specific sub-problem

### Execution at the End

After the structured plan is approved in Phase 5, the skill presents an execution offer. You can:

- `Execute all` -- AI produces all deliverable items
- `Execute [numbers]` -- AI produces specific items
- `Assist [numbers]` -- AI helps with assistable items
- `Done` -- Take the plan and execute on your own

### Exiting and Resuming

When you exit mid-process, the skill summarizes your progress. Re-enter by saying "let's continue the problem architect" or "back to my problem."

---

## 7. Troubleshooting

**"The skill isn't activating"**
Make sure the skill file is properly added to your Project Knowledge or global Settings. Try explicitly saying `/problem-architect` (or `/problemarchitect`).

**"It's jumping to solutions too quickly"**
The skill is designed to resist this, but if it happens, say "let's go back to diagnosing" or "I don't think we've found the root cause yet."

**"The deliverability classification is wrong"**
Challenge it during Phase 3 -- the skill explicitly invites you to correct classifications. Say "I think [item] is actually something you can help with" or vice versa.

**"I want to change my answer from an earlier phase"**
Say "go back to Phase [number]" or "let's revisit the problem statement." The skill will update context accordingly.

**"The problem turned out to be something different"**
This is normal and expected. The skill supports problem pivots -- it will acknowledge the shift and offer to restart or continue with the new framing.

---

## 8. File Structure

```
problem-architect/
├── problem-architect.skill    # ZIP archive containing the Claude skill
│   └── problem-architect/
│       └── SKILL.md           # The Claude skill definition (5-phase problem-solving system)
├── SKILL.md                   # The skill definition (also available standalone)
└── README.md                  # This file
```

To inspect or modify the Claude skill:
1. Rename `.skill` to `.zip` (or just unzip directly)
2. Edit SKILL.md as needed
3. Re-zip the folder and rename back to `.skill`

---

## 9. Version History

**v1.0 (February 2026)**
- Initial release
- 5-phase problem-solving system (Surface, Diagnose, Decompose, Solve, Plan & Execute)
- Research-backed methodology synthesis (JTBD, 5 Whys, Ishikawa, MECE, Constraint Theory, First Principles, Design Thinking)
- Domain adaptation (Technical, Business, Personal, Creative)
- AI deliverability classification and execution offer
- Expedite modes (full/assisted) with prompt-process framework integration
- Context accumulation across phases
- Problem pivot and multi-problem handling

---

## 10. Contact & Support

For questions, improvements, or bug reports, refer to your organization's documentation or the original skill author.
