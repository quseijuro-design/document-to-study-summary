# Page Design

Use this reference when building the study summary page.

## Output Shape

Default output is a browser-openable directory that reuses the `codebase-to-course` shell:

```text
summary-name/
  styles.css
  main.js
  _base.html
  _footer.html
  build.sh
  modules/
    01-center-words.html
    02-storyline.html
    03-dialogue.html
    04-teach-back.html
  index.html
```

Use `modules/` even though the output is a summary, because the shell expects module sections.

## Preferred Asset Source

Reuse these files from:

```text
C:\Users\midor\.codex\skills\codebase-to-course-main\references\
```

Copy:

- `styles.css`
- `main.js`
- `_footer.html`
- `build.sh`

Read `_base.html`, then customize:

- Course title -> summary title.
- Accent palette -> preferably teal, forest, or amber.
- Nav dots -> one per summary section.
- Language -> use `zh-CN` for Chinese summaries.

If Bash is unavailable, assemble `index.html` by concatenating `_base.html`, sorted `modules/*.html`, and `_footer.html` without changing UTF-8 bytes.

## Summary Sections

### 1. Center Words

Start with a direct promise:

```text
读完这页，你应该能用自己的话讲清楚：...
```

Then show 5-9 center words as cards. Each card should include:

- Word.
- Plain-language meaning.
- Why it unlocks the document.
- Source locator.

### 2. Logic Or Storyline

Show the document's movement before details.

Use one of:

- Flow animation for process or argument.
- Static flow steps for narrative arc.
- Comparison grid for competing views.
- Concept map for dense topic clusters.

Keep it tight. A summary page should reveal the skeleton, not rebuild every paragraph.

### 3. Long Dialogue Understanding

Make dialogue longer than `document-to-course` when the user asks for deeper digestion.

Use 8-14 messages by default. Good roles:

- Learner: asks naive but useful questions.
- Explainer: gives plain-language synthesis.
- Skeptic: prevents overclaiming.
- Source voice/author/character/practitioner: brings source-grounded nuance.

Dialogue should:

- Resolve at least two likely confusions.
- Connect center words back to the storyline.
- Include source locators in or near the dialogue section.
- Avoid becoming a generic Q&A detached from the document.

### 4. Visual Anchors

Include either:

- A shot list for Xiaohei-style illustrations.
- Generated images, when explicitly requested or clearly useful and feasible.
- A simple concept map/timeline if images are not generated.

Each visual anchor must help memory or retelling.

### 5. Teach-Back

End with:

- 30-second version.
- 2-minute version.
- 5-minute outline.
- Three self-check questions.
- One "avoid saying it this way" warning.

Read `teach-back.md` for patterns.

## Component Patterns

Use existing shell components:

- `translation-block`: source anchor -> plain explanation.
- `pattern-cards`: center words, misreads, roles, turns.
- `flow-steps` or `flow-animation`: logic/storyline.
- `chat-window`: long dialogue.
- `quiz-container`: self-check questions.
- `term`: glossary tooltip for first-use terms.
- `callout`: thesis, caveat, or source note.

## Final Checks

- A motivated learner can scan the page in 3-7 minutes.
- The first screen says what the document is about.
- Center words appear before long explanation.
- No section is a wall of text.
- Dialogue is helpful and source-grounded.
- The final teach-back section is practical, not motivational filler.
- Text fits on desktop and mobile.
- The page opens from `index.html` without a server.
