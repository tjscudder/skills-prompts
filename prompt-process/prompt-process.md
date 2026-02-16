# Prompt Process Structure

A reusable step-oriented process framework extracted from the `prompt-architect` skill. This document contains only the generic workflow patterns and mechanisms that can be applied to any multi-step interactive skill.

---

## Core Principles

1. **Move strictly step by step** - Never skip ahead to later steps
2. **Complete before proceeding** - Each step must receive APPROVE before moving on
3. **Gather before generating** - Ask questions and accumulate context before drafting outputs
4. **Leverage prior steps** - Use information from earlier steps to maintain consistency
5. **Explicit over implicit** - Never assume unstated requirements; ask when unclear

---

## Workflow Micro-Protocol

At every step, follow this 4-phase micro-protocol:

```
1. ASK      → Present focused questions to gather necessary information
2. REWRITE  → Transform user's answers into structured/optimized output
3. REFLECT  → Briefly explain reasoning (1-2 sentences max)
4. CONFIRM  → Show output and request APPROVE or EDIT
```

**Critical rule:** Only proceed to the next step after receiving APPROVE.

---

## Expedite Mode System

Offer two expedite modes to match user's preferred pace:

| Mode | Behavior |
|------|----------|
| **Expedite: full** | AI drafts all responses; user reviews and approves |
| **Expedite: assisted** | AI offers suggestions on request; user decides what to use (default) |

### Commands Available at Any Step

| Command | Action |
|---------|--------|
| `Suggest all` | Draft responses for all questions in current step |
| `Suggest 1, 3` | Draft responses for specific questions only |
| `Approve` | Accept all suggestions/outputs as-is |
| `1. [response]` | Provide or edit response for question 1 |
| `1. [response]. 2. Suggest` | Mix direct answers with inline Suggest requests |
| `Revise 2: [feedback]` | Ask AI to revise a specific suggestion |

### Command Parsing Rules

- Commands are case-insensitive (`suggest all` = `Suggest All` = `SUGGEST ALL`)
- Numbers can be separated by commas, spaces, or both (`Suggest 1, 3` = `Suggest 1 3`)
- Users can mix commands with direct answers in a single response
- **Inline Suggest:** Users can combine direct answers with Suggest requests
  - Example: `1. My answer here. 2. Suggest. 3. Another answer. 4. Suggest`
  - Process: Accept provided answers directly, generate suggestions only for items marked "Suggest"

---

## Context Accumulation Pattern

Maintain a running context summary updated after each step:

```
CONTEXT_ACCUMULATED:
─────────────────────
- Step 1: [key points from step 1]
- Step 2: [key points from step 2]
- Step 3: [key points from step 3]
- ...
─────────────────────
```

### Using Accumulated Context

When generating drafts or suggestions:
1. Review all accumulated context from prior steps
2. Identify the most relevant points for the current step
3. Generate responses consistent with established information
4. Flag any assumptions where context was insufficient with `⚠️ ASSUMPTION`

---

## Step Presentation Templates

### If Expedite: full

```
STEP [N]: [Step Name]

Based on what we've established:
[Brief summary of relevant prior context]

Here are my suggested responses:

1. [Question 1]
   SUGGESTED: [Draft response based on cumulative context]

2. [Question 2]
   SUGGESTED: [Draft response based on cumulative context]

Please review and either:
- Type "Approve" to accept all suggestions
- Edit any responses inline (e.g., "1. [your edited response]")
- Type "Suggest all" to regenerate all suggestions
```

### If Expedite: assisted

```
STEP [N]: [Step Name]

Questions:
1. [Question 1]
2. [Question 2]
3. [Question 3]

Options:
- Type "Suggest all" to have me draft all responses
- Type "Suggest [numbers]" for specific questions (e.g., "Suggest 1, 3")
- Or answer the questions directly

Your response:
```

---

## Approval Gate Mechanism

### Required Before Proceeding

After each step's output is generated, explicitly request confirmation:

```
Please review and either:
- APPROVE to accept and proceed to the next step
- EDIT: [specific changes] to modify
```

### User Response Handling

| Response | Action |
|----------|--------|
| `APPROVE` | Accept output; proceed to next step |
| `EDIT: [changes]` | Apply changes; re-present output for approval |
| `Revise [N]: [feedback]` | Revise specific item; re-present for approval |

### Enforcement Rules

- Never proceed without explicit APPROVE
- Never finalize outputs without user confirmation
- If user provides partial feedback, apply it and re-confirm

---

## Step Output Format

Each step should produce a structured summary that feeds into context accumulation:

```
[STEP_NAME]_SUMMARY:
- [Key point 1]: [value]
- [Key point 2]: [value]
- [Key point 3]: [value]
```

This format ensures:
- Consistent structure across steps
- Easy reference when generating later outputs
- Clear audit trail of decisions made

---

## Quality Verification (Silent Checks)

Before presenting any output, silently verify:

### Context Completeness
- Have I gathered enough information to generate specific (not generic) outputs?
- If unclear, ask clarifying questions before drafting

### Context Utilization
- Have I incorporated ALL relevant inputs from prior steps?
- Are outputs consistent with previously established decisions?

### Assumption Flagging
- Any assumptions made due to insufficient context should be flagged with `⚠️ ASSUMPTION`
- User should be able to correct assumptions before finalizing

---

## Process Flow Diagram

```
┌─────────────────────────────────────────────────────────────┐
│                      ENTRY POINT                            │
│         Set expedite preference (full or assisted)          │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                      STEP [N]                               │
│                                                             │
│  ┌─────────────────────────────────────────────────────┐   │
│  │ 1. ASK: Present questions                            │   │
│  │    (If expedite:full → include SUGGESTED answers)    │   │
│  └─────────────────────────────────────────────────────┘   │
│                          │                                  │
│                          ▼                                  │
│  ┌─────────────────────────────────────────────────────┐   │
│  │ 2. RECEIVE: User provides answers or uses commands   │   │
│  │    - Direct answers                                  │   │
│  │    - Suggest all / Suggest [N]                       │   │
│  │    - Mix of both                                     │   │
│  └─────────────────────────────────────────────────────┘   │
│                          │                                  │
│                          ▼                                  │
│  ┌─────────────────────────────────────────────────────┐   │
│  │ 3. REWRITE: Transform into structured output         │   │
│  └─────────────────────────────────────────────────────┘   │
│                          │                                  │
│                          ▼                                  │
│  ┌─────────────────────────────────────────────────────┐   │
│  │ 4. REFLECT: Briefly explain reasoning (1-2 sentences)│   │
│  └─────────────────────────────────────────────────────┘   │
│                          │                                  │
│                          ▼                                  │
│  ┌─────────────────────────────────────────────────────┐   │
│  │ 5. CONFIRM: Request APPROVE or EDIT                  │   │
│  └─────────────────────────────────────────────────────┘   │
│                          │                                  │
└──────────────────────────┼──────────────────────────────────┘
                           │
           ┌───────────────┼───────────────┐
           │               │               │
           ▼               ▼               ▼
      [APPROVE]        [EDIT]      [Revise N]
           │               │               │
           │               └───────┬───────┘
           │                       │
           │                       ▼
           │            ┌─────────────────────┐
           │            │ Apply changes,      │
           │            │ return to CONFIRM   │
           │            └─────────────────────┘
           │
           ▼
┌─────────────────────────────────────────────────────────────┐
│            UPDATE CONTEXT_ACCUMULATED                       │
│            Proceed to STEP [N+1]                            │
└─────────────────────────────────────────────────────────────┘
           │
           ▼
    [Repeat until final step]
           │
           ▼
┌─────────────────────────────────────────────────────────────┐
│                    FINAL ASSEMBLY                           │
│  - Review all accumulated context                           │
│  - Generate final deliverable                               │
│  - Apply quality checks                                     │
│  - Present for final APPROVE                                │
└─────────────────────────────────────────────────────────────┘
```

---

## First Message Template

When the skill is triggered, the first message should:

1. Briefly explain (2-4 sentences) what the wizard does and how many steps it includes
2. Mention expedite mode options for faster iteration
3. Present Step 1 questions
4. Wait for user answers, then confirm before proceeding

---

## Key Principles Summary

| Principle | Implementation |
|-----------|----------------|
| **Strict step progression** | Never skip ahead; complete each step before proceeding |
| **User control** | Never proceed without explicit APPROVE |
| **Expedite options** | Offer full/assisted modes to match user pace |
| **Context accumulation** | Maintain running summary; use it to inform all drafts |
| **Inline flexibility** | Allow mixing direct answers with Suggest commands |
| **Brief explanations** | Keep reasoning to 1-2 sentences |
| **Assumption flagging** | Mark any assumptions with ⚠️ for user correction |

---

## Adapting This Process to Other Skills

To apply this process framework to a new skill:

1. **Define your steps** - Identify the logical phases for your domain (can be any number)
2. **Craft step questions** - 3-5 focused questions per step
3. **Design output summaries** - What structured output does each step produce?
4. **Map context accumulation** - What information from each step informs later steps?
5. **Set expedite mode** - Determine if full/assisted modes make sense for your use case
6. **Define final deliverable** - What do users receive at the end?
7. **Add quality checks** - What verification ensures output quality?
