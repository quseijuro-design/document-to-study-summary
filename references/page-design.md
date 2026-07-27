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

When the source is conceptual, argumentative, philosophical, legal, or policy-heavy, prefer a visual argument map over a narrow linear flow. Put the central concept in the middle, show the pressure or tension on both sides, and place the synthesis or learner takeaway below it. At narrow widths, rearrange the map into a readable order instead of simply shrinking it.

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
- A small word/character count or progress indicator.
- A visible evaluation panel that scores whether the retell mentions the center words, storyline, concrete example, caveat, and "so what".
- One stronger sample phrasing that the learner can compare against without copying.

Use the `.retell-workbench` component pattern described below.

## Memory Anchors

Include a simple concept map, timeline, comparison strip, memory-anchor cards, or generated images only when it helps memory or retelling.

Generated Xiaohei-style images are allowed only when the user explicitly asks for images or asks to use the Xiaohei illustration skill.

Do not include a visible "Xiaohei", "小黑配图", or "Shot List" section by default. If images are generated, present each image where it supports the corresponding center word, storyline turn, misread risk, or retell prompt.

Each memory anchor should include:

- the thing to remember
- why it matters
- one sentence the learner can use while retelling

Use this pattern for non-image anchors:

```html
<div class="memory-anchor-card">
  <strong>记住这个画面：...</strong>
  <p>它帮你抓住：...</p>
  <p class="retell-line">复述时可以说：...</p>
</div>
```

Use this pattern for generated images:

```html
<figure class="memory-anchor-image">
  <img src="assets/summary-illustrations/anchor-01.png" alt="...">
  <figcaption>
    <strong>记住这个画面：...</strong>
    <span>它帮你复述：...</span>
  </figcaption>
</figure>
```

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
- `memory-anchor-card`: text-only memory cue for a center word or turn.
- `memory-anchor-image`: generated image plus caption explaining the memory job.
- `misread-grid` and `misread-card`: fixed "do not say / better / why" section.
- `retell-workbench`: textarea plus checklist for speakable retell practice.
- `justice-diagram`: responsive visual argument map for a central idea, two tensions, and the rule/lesson that holds them together.
- `logic-beats`: compact post-diagram beats that explain how the argument moves.
- `balanced-grid`: exactly four peer cards in a stable two-by-two desktop/tablet layout, collapsing to one column on small mobile screens.
- `comparison-callout`: final sample phrasing with a short side label and source-grounded body text.

## Reader-Facing Copy

Everything visible on the generated page should help the learner understand the source document.

Do not expose implementation or design commentary in the learner-facing page. Avoid text such as:

- "fixed 2x2"
- "this grid/layout"
- "this section is designed to"
- "the CSS/component/style"
- "top three, bottom one"

Those notes belong in the skill, not in the study summary. Section subtitles, captions, checklist labels, and sample retell copy should all talk about the document's meaning, logic, examples, risks, and application.

## Responsive Visual Arguments

Use `.justice-diagram` when a document turns on an abstract center idea and opposing pressures. It is useful for law, ethics, governance, philosophy, strategy, and dense essays.

Recommended structure:

```html
<div class="justice-diagram" role="img" aria-label="...">
  <div class="diagram-title">...</div>
  <div class="diagram-side diagram-left">...</div>
  <div class="diagram-center">...</div>
  <div class="diagram-side diagram-right">...</div>
  <div class="diagram-law">...</div>
</div>
```

Design rules:

- Desktop: center the main idea visually; put the two tensions on left and right; put the synthesis below.
- Tablet: keep the center idea above the two tension cards, then the synthesis below.
- Mobile: stack in reading order with no horizontal overflow.
- Use `scroll-margin-top` on targetable visual blocks so sticky navigation does not cover selected elements.
- Check the diagram at desktop, around 614px, and around 390px. The center concept should stay centered inside its container at every width.

## Balanced Card Grids

For exactly four peer items, use `.balanced-grid` instead of a generic auto-fit grid. A three-plus-one card layout looks accidental and makes one item feel secondary.

Use balanced grids for:

- four misread risks
- four retell checklist items
- four comparison points
- four role or argument cards with equal importance

Only use three columns when there are exactly three items or when one item is intentionally featured separately.

## Retell Workbench Markup

Use this shape when building the final module:

```html
<div class="retell-workbench" data-retell-target="120" data-retell-criteria="中心词:...|剧情线:...|例子:...|误读风险:...">
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
  <div class="retell-evaluation">
    <div class="retell-score">
      <span class="retell-score-value">0</span>
      <span class="retell-score-label">retell score</span>
      <span class="retell-score-hint">先写一段，再看缺了什么</span>
    </div>
    <ul class="retell-feedback">
      <li class="todo" data-label="中心词" data-keywords="...">• 中心词</li>
      <li class="todo" data-label="剧情线" data-keywords="...">• 剧情线</li>
      <li class="todo" data-label="具体例子" data-keywords="...">• 具体例子</li>
      <li class="todo" data-label="误读风险" data-keywords="...">• 误读风险</li>
    </ul>
  </div>
</div>
<div class="comparison-callout">
  <div class="comparison-label">可以对照，但不要照抄</div>
  <p>...</p>
</div>
```

## Control Styling

The reused shell may include default browser buttons for chat playback. Replace or override them so they match the summary page:

- Use the page accent color, subtle border, compact radius, and consistent typography.
- Style `Next Message`, `Play All`, and `Reset` as real page controls, not unstyled HTML buttons.
- Keep button text readable on mobile and prevent controls from overlapping message counters.
- Put primary emphasis on `Next Message`; keep secondary playback buttons quieter but still visibly designed.

## Final Checks

- A motivated learner can scan the page in 3-7 minutes.
- The first screen identifies or implies the reading purpose and learner outcome.
- Center words appear before long explanation.
- No section is a wall of text.
- Dialogue is helpful and source-grounded.
- The page includes a fixed misread-risk section.
- The final retell mode is practical and interactive, not motivational filler.
- The retell mode includes visible self-evaluation feedback, not only a textarea and checklist.
- The page does not show raw source ids, page numbers, metadata labels, or citation tags.
- The page does not show a Xiaohei shot-list section unless the user explicitly requested image-generation planning.
- Any visual or generated image has a clear memory job and is placed next to the idea it anchors.
- The page does not contain learner-facing implementation notes such as `2x2`, `layout`, `grid`, `style`, `CSS`, `HTML`, `component`, or `fixed` unless those words come from the source itself.
- Four peer cards are balanced as two-by-two on desktop/tablet and one column on small mobile screens.
- Concept diagrams are checked at desktop, around 614px, and around 390px; no label is clipped, the center idea remains centered, and the diagram has no horizontal overflow.
- Chat controls, retell prompt buttons, checklist cards, retell feedback, comparison callouts, and transitions use the page style instead of browser-default controls.
- Text fits on desktop and mobile.
- The page opens from `index.html` without a server.
