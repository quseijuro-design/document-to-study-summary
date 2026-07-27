# Page Design

Use this reference when building the study summary page.

## Output Shape

Default output is a browser-openable directory that uses this skill's bundled shell:

```text
summary-name/
  styles.css
  main.js
  _base.html
  _footer.html
  build.sh
  modules/
    01-purpose-center-words.html
    02-storyline.html
    03-dialogue.html
    04-misread-risks.html
    05-retell-mode.html
  index.html
```

Use `modules/` even though the output is a summary, because the shell expects module sections.

## Bundled Asset Source

Copy these files from this skill's own `references/` directory:

```text
document-to-study-summary/references/
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

### 1. Purpose And Center Words

Start with a learner-facing orientation:

```text
阅读目标：读完这一页，你应该能用自己的话讲清楚：...
```

Show the inferred purpose as a short badge or sentence, not as metadata. Then show 5-9 center words as cards. Each card should include:

- Word.
- Plain-language meaning.
- Why it unlocks the document.
- How it connects to at least one other center word.
- No visible source/page tag.

For dense documents, add a compact "word map" row:

```text
起点 -> 冲突 -> 转折 -> 代价 -> 结论
```

### 2. Logic Or Storyline

Show the document's movement before details.

Use one of:

- Flow animation for process or argument.
- Static flow steps for narrative arc.
- Comparison grid for competing views.
- Concept map for dense topic clusters.

Keep it tight. A summary page should reveal the skeleton, not rebuild every paragraph.

### 3. Long Dialogue Understanding

Make dialogue longer than `document-to-course` when deeper digestion helps.

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

### 4. Misread Risks

Always include a fixed section named in the output language, such as:

```text
别这样误读
```

Use 2-4 cards. Each card should follow this shape:

```text
不要说：...
更准确：...
为什么：...
```

Good misread cards prevent shallow summaries, overclaims, plot-only retells, or one-sided moral judgments.

### 5. Retell Mode

End with an interactive retell workspace, not only static text. It should include:

- A 30-second prompt.
- A 2-minute structure.
- A 5-minute outline.
- A textarea where the learner can draft their own explanation.
- A checklist for center words, storyline, example, caveat, and "so what".
- A small word/character count or progress indicator when possible.
- One stronger sample phrasing that the learner can compare against without copying.

Use the `.retell-workbench` component pattern described below.

## Visual Anchors

Include a simple concept map, timeline, comparison strip, or visual-anchor cards only when it helps memory or retelling.

Generated Xiaohei-style images are allowed only when the user explicitly asks for images or asks to use the Xiaohei illustration skill.

Do not include a visible "Xiaohei", "小黑配图", or "Shot List" section by default. If images are generated, present the images where they support the corresponding center word or storyline turn.

## Component Patterns

Use existing shell components:

- `translation-block`: source anchor -> plain explanation.
- `pattern-cards`: center words, misreads, roles, turns.
- `flow-steps` or `flow-animation`: logic/storyline.
- `chat-window`: long dialogue.
- `quiz-container`: self-check questions.
- `term`: glossary tooltip for first-use terms.
- `callout`: thesis, caveat, or learner-facing note.

Add these summary-specific components:

- `purpose-strip`: compact reading-purpose orientation near the top.
- `word-map`: center-word chain from starting point to conclusion.
- `misread-grid` and `misread-card`: fixed "do not say / better / why" section.
- `retell-workbench`: textarea plus checklist for speakable retell practice.

## Retell Workbench Markup

Use this shape when building the final module:

```html
<div class="retell-workbench" data-retell-target="120">
  <div class="retell-prompts">
    <button class="btn btn-primary retell-prompt-btn" data-prompt="30s">30 秒</button>
    <button class="btn retell-prompt-btn" data-prompt="2m">2 分钟</button>
    <button class="btn retell-prompt-btn" data-prompt="5m">5 分钟</button>
  </div>
  <p class="retell-current-prompt">用一句话讲清这份材料的核心。</p>
  <textarea class="retell-input" placeholder="试着用自己的话讲一遍..."></textarea>
  <div class="retell-footer">
    <span class="retell-count">0 characters</span>
    <span class="retell-progress">Start with the thesis.</span>
  </div>
  <div class="retell-checklist">
    <label><input type="checkbox"> 我说出了中心词</label>
    <label><input type="checkbox"> 我串起了逻辑/剧情</label>
    <label><input type="checkbox"> 我提到了一个例子</label>
    <label><input type="checkbox"> 我避免了误读</label>
  </div>
</div>
```

## Control Styling

The reused shell may include default browser buttons for chat playback. Replace or override them so they match the summary page:

- Use the page accent color, subtle border, compact radius, and consistent typography.
- Style `Next Message`, `Play All`, and `Reset` as real page controls, not unstyled HTML buttons.
- Keep button text readable on mobile and prevent controls from overlapping message counters.

## Final Checks

- A motivated learner can scan the page in 3-7 minutes.
- The first screen identifies or implies the reading purpose and learner outcome.
- Center words appear before long explanation.
- No section is a wall of text.
- Dialogue is helpful and source-grounded.
- The page includes a fixed misread-risk section.
- The final retell mode is practical and interactive, not motivational filler.
- The page does not show raw source ids, page numbers, metadata labels, or citation tags.
- The page does not show a Xiaohei shot-list section unless the user explicitly requested image-generation planning.
- Text fits on desktop and mobile.
- The page opens from `index.html` without a server.
