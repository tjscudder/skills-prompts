# Master Prompt

> Personal LLM System Prompt Configuration

## 1. Overview

Master Prompt is a personal system prompt configuration that establishes consistent behavior, tone, and interaction style across LLM conversations. Unlike interactive skills, this is an always-on configuration that shapes how the LLM responds in every conversation where it's installed.

### Table of Contents

1. [Overview](#1-overview)
2. [What It Does](#2-what-it-does)
3. [What It Outputs](#3-what-it-outputs)
4. [Setup](#4-setup)
5. [How to Use](#5-how-to-use)
6. [Customization](#6-customization)
7. [Troubleshooting](#7-troubleshooting)
8. [File Structure](#8-file-structure)
9. [Version History](#9-version-history)
10. [Contact & Support](#10-contact--support)

---

## 2. What It Does

The Master Prompt defines the LLM's relationship model, response patterns, and communication style through modular configuration files:

- **Role** - Establishes the relationship model ("trusted companion" vs deferential assistant)
- **Identity** - Captures who you are as a user (background, expertise, tools)
- **Response** - How the LLM should reason, respond, and handle ambiguity
- **Style** - Tone, formatting preferences, and communication rules
- **File Output** - Naming conventions and format rules for generated files
- **Guardrails** - Boundaries, things to avoid, and behavioral constraints

### Key Behaviors

- Leads with concise answers, offers expansion options
- Challenges assumptions and prioritizes accuracy over agreement
- No sycophancy, unnecessary hedging, or preamble
- Dual response model for ambiguous requests
- Direct, peer-level communication

---

## 3. What It Outputs

This is not a wizard or interactive skill -- it doesn't produce a deliverable. Instead, it shapes the LLM's behavior throughout the conversation by establishing:

- Consistent communication style and tone
- Response formatting preferences
- File naming conventions (`[topicDescription]_[YYYYMMDD].[ext]` in camelCase)
- Guardrails and behavioral boundaries

---

## 4. Setup

### Option 1: Single File (Recommended)

Use `master-prompt.md` directly. It contains the complete assembled prompt.

1. Open Claude.ai and navigate to your Project (or create a new one)
2. In the Project Knowledge section, click "Add content"
3. Upload or paste the contents of `master-prompt.md` into the Project Instructions
4. The configuration is now active for all conversations in that Project

### Option 2: Global Installation

To apply across ALL conversations:

1. Open Claude.ai and click on your profile icon (bottom-left)
2. Select "Settings"
3. Navigate to "Capabilities" or "Custom Instructions"
4. Paste the contents of `master-prompt.md`
5. Save your settings

### Option 3: Modular Composition

For different contexts, combine individual module files as needed:

1. Always start with `00-role.md` (sets the relationship frame)
2. Include remaining numbered files in order (`01-identity.md` through `04-file-output.md`)
3. Always include `guardrails.md`
4. Combine and paste into your Project Instructions or Settings

---

## 5. How to Use

Once installed, the Master Prompt works automatically. There are no commands to invoke -- it shapes every response in the conversation.

The LLM will:
- Lead with direct, concise answers
- Offer to expand on topics when depth is available
- Challenge assumptions when accuracy matters
- Use the defined file naming conventions for any generated files
- Follow the guardrails and communication preferences you've set

---

## 6. Customization

### Editing Modules

Each aspect of the configuration is stored in a separate file. To customize:

- Edit the relevant module file (e.g., `03-style.md` for tone changes)
- Reassemble `master-prompt.md` by combining all modules in order
- Re-upload to your Project or Settings

### Composition Rules

When assembling a full prompt:
1. Always start with `00-role.md` (sets the relationship frame)
2. Include remaining numbered files in numerical order
3. Always include `guardrails.md`
4. Add domain-specific or template sections as needed
5. For non-Claude LLMs, adjust syntax if needed

---

## 7. Troubleshooting

**"The LLM isn't following the style preferences"**
Make sure `master-prompt.md` is in the Project Instructions (not just Knowledge). Instructions take priority over Knowledge files.

**"I want different behavior in different projects"**
Use the modular approach -- include only the modules relevant to each project context.

**"The file naming convention isn't being followed"**
Ensure `04-file-output.md` is included in your assembled prompt. Some LLMs may need explicit reminders for file naming.

**"The LLM is too direct / not direct enough"**
Edit `03-style.md` to adjust the tone and communication preferences, then reassemble.

---

## 8. File Structure

```
master-prompt/
├── master-prompt.md    # Complete assembled prompt (use this for single-file setup)
├── 00-role.md          # Relationship model and persona
├── 01-identity.md      # Who you are as a user
├── 02-response.md      # How the LLM should respond and reason
├── 03-style.md         # Tone and formatting preferences
├── 04-file-output.md   # File naming and format rules
├── guardrails.md       # What to avoid, boundaries
└── README.md           # This file
```

---

## 9. Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.1.0 | 2026-01-31 | Restructured via Prompt Architect; elevated role to standalone module; added dual response example |
| 1.0.0 | 2026-01-31 | Initial release |

---

## 10. Contact & Support

For questions, improvements, or bug reports, refer to your organization's documentation or the original skill author.
