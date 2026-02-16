# Deep Dive Skill

> Progressive Topic Learning System

## 1. Overview

Deep Dive is a progressive topic learning system that takes you from zero to deep understanding of any subject through structured phases. It transforms any conversation into a guided learning experience, moving from high-level orientation to expert-level nuance at your pace.

Based on Bruner's Spiral Curriculum (revisiting concepts at increasing depth) and the Dreyfus skill acquisition model (novice to expert).

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

The skill guides you through four learning phases, each building on the last:

1. **Phase 1 -- Orientation** ("Cocktail Party" level) - You can explain the topic in 2-3 sentences. Covers: definition, why it exists, key terms, and a grounding analogy.
2. **Phase 2 -- Mechanics** ("I Actually Understand This" level) - You have a working mental model. Covers: conceptual framework, core principles, connections, misconceptions, and a worked example.
3. **Phase 3 -- Application** ("I Can Use This" level) - You can apply the knowledge. Covers: usage patterns, decision frameworks, step-by-step walkthroughs, pitfalls, and tools.
4. **Phase 4 -- Expert Territory** ("I Can Discuss This with Specialists" level) - You understand the nuances. Covers: internals, tradeoffs, current state, open questions, and further learning resources.

### Core Principles

- **Progressive disclosure** -- start broad, go deep only when requested
- **Learner controls pace** -- never advance without explicit signal
- **Branch, don't just descend** -- offer multiple directions at each phase
- **Anchor to the known** -- connect new concepts to what you already understand
- **Context preservation** -- learning happens inline; the conversation continues naturally

---

## 3. What It Outputs

At each phase, the skill produces a structured response at the appropriate depth level, followed by navigation options. You control what happens next -- advance, branch into subtopics, ask questions, skip ahead, or exit.

At any point you can request a **Summary & Resources** reference that includes:
- One-sentence definition
- Key concepts
- Mental model
- Decision framework
- Common pitfalls
- Resources for further learning

---

## 4. Installation: Claude.AI

### Option 1: Project-Specific Installation

1. Open Claude.ai and navigate to your Project (or create a new one)
2. In the Project Knowledge section, click "Add content"
3. Upload the `SKILL.md` file
4. The skill is now available in that Project's conversations

### Option 2: Global Installation

1. Open Claude.ai and click on your profile icon (bottom-left)
2. Select "Settings"
3. Navigate to "Capabilities" or "Custom Instructions"
4. Upload or paste the contents of `SKILL.md`
5. Save your settings

### Option 3: Manual Installation (Copy/Paste)

1. Open `SKILL.md` and copy the entire contents
2. Paste into either:
   - Settings > Capabilities (for global access), or
   - Project Knowledge (for project-specific access)

---

## 5. Triggering the Skill

Use one of these triggers in any conversation:

- `/deep-dive`
- "Deep dive into [topic]"
- "Teach me about [topic]"
- "Explain [topic]"
- "What is [topic]"
- "How does [topic] work"
- "I want to understand [topic]"
- "Walk me through [topic]"
- "Help me learn about [topic]"

The skill will confirm the topic and begin at Phase 1.

If you're already mid-conversation about a topic, the skill will infer the topic from context and confirm before starting.

---

## 6. How to Use the Skill

### Starting a Session

Simply name the topic you want to learn about:

> "Deep dive into quantum computing"

The skill begins at Phase 1 (Orientation) and presents navigation options at the end of each phase.

### Navigating Between Phases

At the end of each phase, you'll see numbered options. Choose by number or describe what you want:

- **Advance** to the next phase
- **Branch** into a subtopic at the current depth
- **Ask questions** (answered at the current phase's level)
- **Skip ahead** to a later phase
- **Exit** and continue the conversation normally

### Comprehension Checks

At any phase, say "let me explain it back" or "check my understanding." The skill will:
1. Invite you to explain the concept
2. Give specific feedback: what you got right, what needs refinement, and what's missing
3. Offer to revisit areas where understanding is shaky

### Branching into Subtopics

When you branch into a subtopic, the skill restarts the phase structure for that subtopic at a compressed scale. The nesting is shown:

```
Phase 2 of 4 -- Mechanics
Topic: Quantum Computing > Quantum Error Correction
```

### Exiting

When you exit, the skill summarizes where you got to and what you covered. You can re-enter at any time by saying "let's continue the deep dive" or "back to learning about [topic]."

---

## 7. Troubleshooting

**"The skill isn't activating"**
Make sure the SKILL.md file is properly added to your Project Knowledge or global Settings. Try explicitly saying `/deep-dive` or "deep dive into [topic]".

**"The content is too basic / too advanced"**
The skill adapts to contextual cues. If you're clearly technical, mention your background. You can also skip ahead to later phases at any time.

**"I want to go back to an earlier phase"**
Say "go back to Phase [number]" or "let's revisit the basics."

**"I want a summary of what I've learned"**
Say "summary and resources" at any point to get a structured reference.

---

## 8. File Structure

```
deep-dive/
├── SKILL.md     # The skill definition (4-phase learning system)
└── README.md    # This file
```

---

## 9. Version History

**v1.0 (January 2026)**
- Initial release
- 4-phase progressive learning system
- Comprehension checks with honest feedback
- Subtopic branching with compressed phases
- Summary & Resources generation at any phase
- Based on Bruner's Spiral Curriculum and Dreyfus skill acquisition model

---

## 10. Contact & Support

For questions, improvements, or bug reports, refer to your organization's documentation or the original skill author.
