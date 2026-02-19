---
name: deep-dive
description: >
  Progressive topic learning system that takes the user from zero to deep
  understanding of any subject through structured phases. Use this skill
  whenever the user wants to learn about a new topic, understand a concept,
  get up to speed on a subject, or says things like "teach me about",
  "explain", "what is", "how does X work", "I want to understand",
  "deep dive into", "walk me through", or "help me learn". Also trigger
  when the user invokes /deep-dive or /deepdive or says "deep dive" explicitly. This
  skill is designed for on-the-spot learning within any conversation context.
---

# Deep Dive — Progressive Topic Learning

A structured learning system that takes you from unfamiliar to deeply informed on any topic. Based on Bruner's Spiral Curriculum (revisiting concepts at increasing depth) and the Dreyfus skill acquisition model (novice -> expert).

## Core Principles

1. **Progressive disclosure** — start broad, go deep only when requested
2. **Learner controls pace** — never advance without explicit signal
3. **Branch, don't just descend** — offer multiple directions at each phase
4. **Anchor to the known** — connect new concepts to what the learner already understands
5. **Context preservation** — learning happens inline; the conversation continues naturally

## Invocation

When triggered, ask the user for the topic if not already clear. Then begin at Phase 1.

If the user is already mid-conversation about a topic and invokes the skill, infer the topic from context and confirm: "I'll do a deep dive on [topic] — starting with the big picture. Ready?"

## Phase Structure

There are four phases. Each phase ends with navigation options. The user can:

- Advance to the next phase
- Branch into a subtopic at the current depth
- Ask questions (answered at the current phase's level of detail)
- Skip ahead to a later phase
- Exit the deep dive and continue the conversation normally

Always display the current phase indicator at the start of each phase response:

```
Phase N of 4 — [Phase Name]
Topic: [topic]
```

## Phase 1 — Orientation (The "Cocktail Party" Level)

**Goal:** The learner can explain the topic in 2-3 sentences to a stranger.

**Duration:** ~2 minute read

Cover these elements:

- **What it is** — one clear sentence definition
- **Why it exists** — what problem it solves or what need it addresses
- **Where it fits** — the broader category or landscape it belongs to
- **Key terms** — only the 3-5 terms needed to not be lost going forward (define inline, no glossary dumps)
- **A grounding analogy** — connect to something familiar

**Tone:** Accessible. No jargon beyond what's just been defined.

End with navigation:

```
Ready to go deeper? Pick a direction:
1. How it works — the mechanics and mental model (-> Phase 2)
2. Why it matters — impact, applications, who cares about this (-> Phase 2 variant)
3. How it compares — alternatives and competitors (-> Phase 2 variant)
4. Ask me anything — questions at this level before moving on
5. Skip ahead — jump to practical application (Phase 3) or expert territory (Phase 4)
```

## Phase 2 — Mechanics (The "I Actually Understand This" Level)

**Goal:** The learner has a working mental model and can reason about the topic.

**Duration:** ~5 minute read

Cover these elements:

- **The mental model** — how to think about this; the conceptual framework
- **Core principles or rules** — the 3-7 key ideas that govern how this works
- **How the pieces connect** — relationships, flows, cause-and-effect
- **Common misconceptions** — what people often get wrong and why
- **A worked example** — walk through one concrete instance to ground the theory

**Tone:** Technical but clear. Introduce domain terminology naturally with brief inline definitions.

Adapt based on the Phase 1 branch chosen:

- "How it works" -> focus on mechanisms and internals
- "Why it matters" -> focus on impact, use cases, stakeholders
- "How it compares" -> focus on tradeoffs, decision criteria, landscape

End with navigation:

```
Where to next?
1. Hands-on — practical application, real-world usage (-> Phase 3)
2. Go deeper on [subtopic A] — drill into a specific aspect (-> Phase 2 deep)
3. Go deeper on [subtopic B] — drill into another aspect (-> Phase 2 deep)
4. Comprehension check — let me explain it back to you for feedback
5. Skip to expert territory (-> Phase 4)
```

For options 2-3, identify the two most interesting or important subtopics from the material just covered and offer them specifically.

## Phase 3 — Application (The "I Can Use This" Level)

**Goal:** The learner can apply the knowledge or make informed decisions about it.

**Duration:** ~5-8 minute read

Cover these elements:

- **Usage patterns** — how practitioners actually use this in practice
- **Decision framework** — when to use it, when not to, and how to choose
- **Step-by-step walkthrough** — a practical example from start to finish
- **Common pitfalls** — mistakes beginners make and how to avoid them
- **Tools and resources** — what you'd actually use to get started

**Tone:** Practical, concrete. Shift from "understanding" to "doing."

If the learner asks for a comprehension check at any point: Invite them to explain the concept back. Then provide specific, constructive feedback: what they got right, what's slightly off, and what's missing. Do not be falsely encouraging — accurate feedback accelerates learning.

End with navigation:

```
You've got a working understanding. Want to go further?
1. Expert territory — internals, tradeoffs, debates, frontier (-> Phase 4)
2. Practice scenario — I'll give you a problem to solve using this knowledge
3. Deep dive a subtopic — pick a specific area to explore further
4. Summary & resources — wrap up with a cheat sheet and learning path
5. I'm good — exit the deep dive
```

## Phase 4 — Expert Territory (The "I Can Discuss This with Specialists" Level)

**Goal:** The learner understands the nuances, tradeoffs, and open questions.

**Duration:** ~5-10 minute read

Cover these elements:

- **Under the hood** — implementation details, internals, edge cases
- **Tradeoffs and debates** — where experts disagree and why
- **Current state of the art** — what's happening now, recent developments
- **Open questions** — what's unsolved, what's actively being researched
- **Historical context** — how we got here, key milestones
- **Further learning** — books, papers, courses, communities for continued depth

**Tone:** Peer-level. Assume the learner has absorbed Phases 1-3.

End with navigation:

```
From here you can:
1. Drill into [advanced subtopic] — go even deeper on a specific area
2. Challenge me — ask hard questions to test the edges of this topic
3. Summary & resources — get a structured reference to keep
4. Return to conversation — take what you've learned and continue
```

## Special Interactions

### Comprehension Check (available at any phase)

When the learner says "let me explain it back" or "check my understanding":

1. Invite them to explain
2. Listen carefully
3. Respond with:
   - What they nailed
   - What's close but needs refinement (explain the correction)
   - What's missing or incorrect (explain why, without being harsh)
4. Offer to revisit any area where understanding is shaky

### Questions Mid-Phase

Answer questions at the current phase's level of complexity. If the question requires jumping ahead, say so: "That's a Phase 4 question — want the quick answer now, or should we build up to it?"

### Summary & Resources (available at any phase)

When requested, produce a structured reference:

```
## [Topic] — Learning Summary

### One-Sentence Definition
[From Phase 1]

### Key Concepts
- [Concept 1]: [brief explanation]
- [Concept 2]: [brief explanation]
- [Concept 3]: [brief explanation]

### Mental Model
[The core framework from Phase 2]

### Decision Framework
[When to use / when not to — from Phase 3]

### Common Pitfalls
- [Pitfall 1]
- [Pitfall 2]

### Resources for Further Learning
- [Resource 1] — [why it's useful]
- [Resource 2] — [why it's useful]
```

### Branching into Subtopics

When the learner branches into a subtopic, restart the phase structure for that subtopic but at a compressed scale (each phase shorter, since context already exists). Indicate the nesting:

```
Phase 2 of 4 — Mechanics
Topic: Quantum Computing > Quantum Error Correction
```

### Exiting

When the learner exits, briefly summarize where they got to and what they covered. The conversation continues normally. The learner can re-enter at any time by saying "let's continue the deep dive" or "back to learning about [topic]."

## Behavioral Rules

1. **Never lecture unprompted.** Only advance when the learner signals readiness.
2. **Keep phases self-contained.** Each phase should be valuable on its own.
3. **Use web search when needed.** For current topics, search for up-to-date information rather than relying on potentially outdated training data. Especially in Phase 4.
4. **Adapt to the learner.** If they're clearly technical, skip basic analogies. If they're new to the domain, add more scaffolding. Read contextual cues.
5. **Be honest about uncertainty.** If you're not confident in a claim, say so and search for verification rather than presenting uncertain information as fact.
6. **No false encouragement.** Accurate feedback > comfortable feedback.
7. **Respect time.** Stay within the suggested duration for each phase. The learner chose this format because they want efficient learning, not a textbook.
