# Purpose And Modes

Use this reference to infer why the learner is reading and to adapt the summary without asking unnecessary questions.

## Purpose Detection

Infer the reading purpose from the user's words, source type, and surrounding context. If the purpose is ambiguous, use `general quick understanding` and make the summary broadly useful.

Do not stop to ask unless the user's purpose would materially change the output, such as choosing between exam drilling and literary interpretation.

## Purpose Profiles

### General Quick Understanding

Use when the user asks to understand, summarize, learn, or retell a document.

Emphasize:

- one-sentence promise
- center words
- logic/storyline
- likely misreads
- 30-second and 2-minute retell

### Interview Or Exam Prep

Use when the user mentions interview, exam, high-frequency questions, memorization, or preparation.

Emphasize:

- testable definitions
- compare/contrast points
- common traps
- answer templates in the learner's own words
- quick self-check questions

### Literature Or Narrative

Use for novels, memoirs, essays, poems, narrative nonfiction, or character-driven documents.

Emphasize:

- central words as themes, conflicts, and symbols
- storyline turns rather than full plot reconstruction
- character desire, cost, recognition, and misread risks
- speakable interpretation rather than plot recap

### Technical Or Operational Document

Use for manuals, API docs, policies, processes, architecture notes, and how-to material.

Emphasize:

- goal and done state
- prerequisites
- process steps
- failure modes
- what to say to an AI/tool/person when using the document

### Business Or Research Report

Use for market reports, research papers, strategy docs, and business analysis.

Emphasize:

- claim
- evidence
- caveats
- decision implications
- what not to overclaim

### Existing Course Compression

Use when the input is a generated course or learning module.

Emphasize:

- final capability
- repeated patterns across modules
- what can be skipped
- what must be remembered
- a compact retell of the whole course

## Output Rule

Show the purpose lightly near the top as a learner-facing orientation, not as metadata. Good labels:

```text
阅读目标：快速讲清这份材料
阅读目标：面试前能答出来
阅读目标：理解人物命运和主题
```

Avoid technical labels such as `purpose_profile: literature`.
