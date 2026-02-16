# Prompt Process Framework

> Reusable Step-Oriented Workflow for Multi-Step Interactive Skills

## 1. Overview

Prompt Process is a generic workflow framework extracted from the Prompt Architect skill. It defines the step-by-step interaction patterns, command systems, and quality mechanisms that can be applied to any multi-step interactive skill.

This is not a skill itself -- it's a blueprint for building new skills that follow a consistent, proven interaction model.

### Table of Contents

1. [Overview](#1-overview)
2. [What It Contains](#2-what-it-contains)
3. [How to Use](#3-how-to-use)
4. [File Structure](#4-file-structure)
5. [Version History](#5-version-history)
6. [Contact & Support](#6-contact--support)

---

## 2. What It Contains

The framework defines these reusable patterns:

- **Workflow Micro-Protocol** - The 4-phase cycle every step follows: ASK, REWRITE, REFLECT, CONFIRM
- **Expedite Mode System** - Two speed modes (full/assisted) with commands like `Suggest all`, `Approve`, `Revise`, and inline suggest
- **Context Accumulation Pattern** - How to maintain a running summary across steps for consistency
- **Approval Gate Mechanism** - Enforcing explicit user approval before proceeding
- **Step Presentation Templates** - Ready-to-use templates for both expedite modes
- **Quality Verification** - Silent checks for context completeness, utilization, and assumption flagging
- **Process Flow Diagram** - Visual diagram of the complete interaction flow

---

## 3. How to Use

### Building a New Skill

Use `prompt-process.md` as a reference when designing any multi-step interactive skill:

1. **Define your steps** - Identify the logical phases for your domain (can be any number)
2. **Craft step questions** - 3-5 focused questions per step
3. **Design output summaries** - What structured output does each step produce?
4. **Map context accumulation** - What information from each step informs later steps?
5. **Set expedite mode** - Determine if full/assisted modes make sense for your use case
6. **Define final deliverable** - What do users receive at the end?
7. **Add quality checks** - What verification ensures output quality?

### Reference for Existing Skills

The Prompt Architect and Project Architect skills both implement this framework. Refer to their SKILL.md files for concrete examples of the patterns in action.

---

## 4. File Structure

```
prompt-process/
├── prompt-process.md    # The complete framework document
└── README.md            # This file
```

---

## 5. Version History

**v1.0 (January 2026)**
- Extracted from Prompt Architect skill as a standalone framework
- Includes micro-protocol, expedite mode, context accumulation, approval gates
- Process flow diagram and step presentation templates
- Adaptation guide for building new skills

---

## 6. Contact & Support

For questions, improvements, or bug reports, refer to your organization's documentation or the original skill author.
