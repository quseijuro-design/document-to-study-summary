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
- No visible source/page tag.

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
- Stay source-grounded without showing raw page numbers or source ids.
- Avoid becoming a generic Q&A detached from the document.

### 4. Visual Anchors

Include either:

- A simple concept map, timeline, comparison strip, or visual-anchor cards.
- Generated Xiaohei-style images only when the user explicitly asks for images or asks to use the Xiaohei illustration skill.

Each visual anchor must help memory or retelling.

Do not include a visible "Xiaohei", "小黑配图", or "Shot List" section by default. If images are generated, present the images where they support the corresponding center word or storyline turn.

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
- `callout`: thesis, caveat, or learner-facing note.

## Control Styling

The reused shell may include default browser buttons for chat playback. Replace or override them so they match the summary page:

- Use the page accent color, subtle border, compact radius, and consistent typography.
- Style `Next Message`, `Play All`, and `Reset` as real page controls, not unstyled HTML buttons.
- Keep button text readable on mobile and prevent controls from overlapping message counters.

## Final Checks

- A motivated learner can scan the page in 3-7 minutes.
- The first screen says what the document is about.
- Center words appear before long explanation.
- No section is a wall of text.
- Dialogue is helpful and source-grounded.
- The final teach-back section is practical, not motivational filler.
- The page does not show raw source ids, page numbers, metadata labels, or citation tags.
- The page does not show a Xiaohei shot-list section unless the user explicitly requested image-generation planning.
- Text fits on desktop and mobile.
- The page opens from `index.html` without a server.
