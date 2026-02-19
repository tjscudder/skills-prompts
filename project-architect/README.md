# Project Architect Skill

> README & Guide

## 1. Overview

Project Architect is an interactive 4-step wizard that guides you through creating or refining Claude Project configurations, producing production-ready Title, Description, Instructions, and knowledge base recommendations.

Instead of setting up projects from scratch, this skill interviews you about your goals, requirements, and resources, then assembles a well-structured project configuration tailored to your needs using Anthropic's best practices.

### Table of Contents

1. [Overview](#1-overview)
2. [What It Does](#2-what-it-does)
3. [What It Outputs](#3-what-it-outputs)
4. [Installation: Claude.AI](#4-installation-claudeai)
5. [Triggering the Skill](#5-triggering-the-skill)
6. [How to Use the Skill](#6-how-to-use-the-skill)
7. [Operating Modes](#7-operating-modes)
8. [Troubleshooting](#8-troubleshooting)
9. [File Structure](#9-file-structure)
10. [Version History](#10-version-history)
11. [Contact & Support](#11-contact--support)

---

## 2. What It Does

The skill operates in two modes depending on your context:

### New Project Setup Mode

For creating new Claude Projects from scratch:

1. **Purpose & Scope** - What problem you're solving, tasks, audience
2. **Requirements & Constraints** - Output formats, rules, boundaries
3. **Knowledge & Resources** - Reference materials, context reliance, skills
4. **Final Assembly** - Generates complete project configuration

### Existing Project Refinement Mode

For improving existing Claude Projects:

1. **Analyze Current State** - Review existing setup and configuration
2. **Identify Evolution** - Discover changes, gaps, and new needs
3. **Propose Updates** - Draft targeted improvements
4. **Final Assembly** - Present all changes for approval

At each step, the skill asks questions, rewrites your answers into optimized configuration text, explains its reasoning, and asks for your approval before moving on.

### Expedite Mode

The skill supports two speed modes to match your preferred pace:

- **Expedite: full** - AI drafts all responses; you review and approve
- **Expedite: assisted** - AI offers suggestions; you decide what to use (default)

You'll select your Expedite Mode when the wizard begins.

Commands available at any step:

- `Suggest all` - Draft responses for all questions
- `Suggest 1, 3` - Draft responses for specific questions
- `Approve` - Accept all suggestions
- `1. [response]` - Provide/edit response for question 1
- `Revise 2: [feedback]` - Ask AI to revise a specific suggestion

### Inline Suggest (Mix answers with suggestions)

You can combine your own answers with Suggest requests in a single response:

**Example:** `1. Customer support. 2. Suggest. 3. API docs. 4. Suggest`

This tells the skill to:
- Accept your direct answers for questions 1 and 3
- Generate AI suggestions only for questions 2 and 4

This is useful when you know some answers but want help with others.

---

## 3. What It Outputs

The skill generates a complete Claude Project configuration including:

- **Project Title** - Descriptive name for your project
- **Project Description** - Brief summary of purpose and capabilities
- **Project Instructions** - Comprehensive setup following best practices:
  - Role definition
  - Context and objectives
  - Guidelines and constraints
  - Output format specifications
  - Example interactions (if applicable)
- **Knowledge Base Recommendations** - Files, documents, and skills to include
- **Starter Templates** - Ready-to-use prompt templates (if applicable)

### Final Deliverable Format

The final output is presented in a structured format ready for copy/paste into your Claude Project settings:

```
PROJECT_TITLE: [Generated title]

PROJECT_DESCRIPTION: [Generated description]

PROJECT_INSTRUCTIONS:
[Complete instructions block]

KNOWLEDGE_BASE_RECOMMENDATIONS:
[List of recommended files, documents, and skills]

STARTER_TEMPLATES (if applicable):
[Ready-to-use prompt templates]
```

---

## 4. Installation: Claude.AI

### Option 1: Global Installation (All Chats)

To make the skill available across ALL your Claude conversations:

1. Open Claude.ai and click on your profile icon (bottom-left)
2. Select "Settings"
3. Navigate to the "Capabilities" section
4. Under Skills or Custom Instructions, click "Add" or "Upload"
5. Upload the `project-architect.skill` file (Claude will extract and read the SKILL.md inside)
6. Save your settings
7. The skill is now available in ALL your conversations, not just projects

### Option 2: Project-Specific Installation

To use this skill only within a specific Project:

1. Open Claude.ai and navigate to your Project (or create a new one)
2. In the Project Knowledge section, click "Add content"
3. Select "Upload files" and choose the `project-architect.skill` file (Claude will extract and read the SKILL.md inside)
4. The skill is now available in that Project's conversations only

### Option 3: Manual Installation (Copy/Paste)

If file upload isn't working, you can add the skill manually:

1. Unzip the .skill file (it's a ZIP archive -- rename to .zip if needed)
2. Open the extracted `project-architect/SKILL.md` file
3. Copy the entire contents
4. Paste into either:
   - Settings > Capabilities (for global access), or
   - Project Knowledge (for project-specific access)

---

## 5. Triggering the Skill

Start a new conversation and use one of these triggers:

- `/project-architect` or `/projectarchitect`
- "Help me set up a new project"
- "Create a project for [your use case]"
- "New project wizard"
- "Update this project's setup"

Claude will recognize the skill and begin the appropriate wizard mode.

---

## 6. How to Use the Skill

### Starting a Session

Simply describe what you need, for example:

> "I need to create a project for code reviews and architecture planning"

Or just say `/project-architect` (or `/projectarchitect`) and the wizard will ask what you're building.

### During the Interview

At each step, the skill will:

1. Ask you focused questions
2. Rewrite your answers into configuration text
3. Explain why it made certain choices (1-2 sentences)
4. Show you the result and ask for approval

Respond with:
- **APPROVE** (or just "yes", "looks good", etc.) to accept and continue
- **EDIT: [your changes]** to modify before proceeding

### Context Accumulation

The skill maintains a running summary of all your responses, using prior step information to inform suggestions and maintain consistency throughout the wizard.

### Reviewing the Final Output

In Step 4 (Final Assembly), review the complete project configuration. You can:

- Request changes to specific sections
- Ask to expand or tighten certain areas
- Adjust the structure or wording

Only approve when you're satisfied with the result.

### Tips for Best Results

- Be specific about your use case and target audience
- Mention any existing documents, guides, or skills you want to include
- Specify any constraints or standards that must be followed
- Describe what Claude should avoid doing or saying

---

## 7. Operating Modes

The skill automatically detects which mode to use based on context:

### New Project Setup

Triggered when:
- Starting in a new/empty project
- Describing a new project idea
- Explicitly requesting to "create" or "set up" a project

This mode guides you through defining everything from scratch.

### Existing Project Refinement

Triggered when:
- Working in a project with existing instructions
- Project has knowledge base content
- Project has conversation history
- Explicitly requesting to "update" or "refine" the project

This mode analyzes what you have and proposes targeted improvements rather than wholesale rewrites.

### Key Difference

- **New Project:** Builds configuration from the ground up
- **Refinement:** Preserves what works, fixes what doesn't

---

## 8. Troubleshooting

**"The skill isn't activating"**
Make sure the skill file is properly added to your Project Knowledge or global Settings. Try explicitly saying `/project-architect` (or `/projectarchitect`) or "use the project architect skill".

**"I want to restart from a specific step"**
Say "Let's go back to Step [number]" or "I want to redo the [section name]".

**"The suggestions don't match my needs"**
Provide more specific context about your requirements. You can also use `Revise [number]: [feedback]` to ask for targeted revisions.

**"I need to edit the final configuration"**
You can ask Claude to modify specific sections even after the final output. Just say "Edit the instructions section to add..." or similar.

**"The skill detected the wrong mode"**
Explicitly state your intent: "I want to create a new project" or "I want to refine this existing project".

**"How do I apply the generated configuration?"**
After approval, copy the relevant sections:
1. Project Title and Description go in your project settings
2. Project Instructions go in the "Custom Instructions" field
3. Knowledge Base items should be uploaded to Project Knowledge

---

## 9. File Structure

```
project-architect/
├── project-architect.skill    # ZIP archive containing the Claude skill
│   └── project-architect/
│       └── SKILL.md           # The Claude skill definition (4-step)
└── README.md                  # This file
```

To inspect or modify the Claude skill:
1. Rename `.skill` to `.zip` (or just unzip directly)
2. Edit SKILL.md as needed
3. Re-zip the folder and rename back to `.skill`

---

## 10. Version History

**v1.0 (January 2026)**
- Initial release
- 4-step interactive wizard for new project setup
- 4-step wizard for existing project refinement
- Expedite Mode support (full/assisted)
- Context accumulation across steps
- Inline Suggest capability for mixing answers with suggestions
- Assumption flagging with visual indicators
- Supports knowledge base and skill recommendations

---

## 11. Contact & Support

For questions, improvements, or bug reports, refer to your organization's documentation or the original skill author.
