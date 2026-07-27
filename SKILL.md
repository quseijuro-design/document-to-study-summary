---
name: document-to-study-summary
description: "Turn documents, PDFs, DOCX files, Markdown notes, web pages, reports, courses, novels, essays, manuals, or document folders into a concise source-grounded study summary page. Use when someone wants to quickly understand a document, extract central words or themes, connect ideas in a logical or narrative storyline, make a clean visual learning summary with memory-anchor images, create a longer dialogue-style explanation, identify the learner's reading purpose, avoid common misreadings, practice an interactive teach-back/retell mode, optionally generate Xiaohei-style memory-anchor images when explicitly requested, or help the learner retell the document in their own words."
---

# Document To Study Summary

Transform one document, a document set, or an existing generated course into a compact, browser-openable learning summary. The goal is fast understanding and teach-back: after reading the page, the learner should be able to explain the document in their own words.

This skill ships with its own browser page shell and interaction assets, adapted from the course shell but tuned for study summaries: reading purpose, central words, logical storyline, long dialogue, misread prevention, memory anchors, and retell practice.

## First-Run Welcome

When the skill is triggered and the user has not provided a document, course, folder, or URL yet, say briefly:

> I can turn a document or course into a concise study summary page.
>
> Point me at a PDF, DOCX, Markdown file, web page, notes folder, or generated course. I will extract the central words, connect them into the document's logic or storyline, build a clean interactive page, and end with a teach-back script so you can explain it in your own words.

If the user says "this document", "this course", "this page", or similar, use the attached file, current browser page, or current working directory as the source when available.

## Core Rules

- Ground every substantive point in the source.
- Prefer paraphrase and synthesis over long quotation.
- For copyrighted long-form works, do not reconstruct the whole source as a substitute for reading it. Teach structure, themes, logic, and selected short anchors.
- Track source locators internally: file name, heading, PDF page, module title, section title, or URL.
- Do not show technical source labels in the final learner page, such as `S1`, `p. 6`, `pp. 8-25`, `Source:`, `metadata`, or raw locator tags. Use source locators for grounding and verification, not as visible study-summary copy.
- Do not show page-building commentary in the final learner page. Visible copy should explain the document, not the implementation. Avoid words such as `2x2`, `layout`, `grid`, `style`, `CSS`, `HTML`, `component`, `fixed`, or notes about how a section was designed unless those words are part of the source itself.
- Separate source facts from interpretation when the distinction matters.
- Make the output concise enough to scan, but rich enough to support retelling.
- Build the summary page after analysis; do not stop at an outline unless the user asks for one.

## Workflow

### Phase 1: Gather Source

Identify the input:

- PDF/DOCX/Markdown/TXT/HTML: extract text and source locators.
- Existing course directory: inspect `index.html`, module files, headings, quizzes, dialogue, and source tags.
- Web page: browse only when the user provided a URL or explicitly asked to use the web.
- Folder: inventory with `rg --files`, then choose canonical entry points.

For extraction and center-word analysis, read `references/analysis-and-center-words.md`.

### Phase 2: Build The Study Map

Create a compact internal map:

```text
Source promise:
Reading purpose:
Learner outcome:
Central words:
Logic/storyline:
Key turns:
Characters/actors/roles:
Tensions or tradeoffs:
Misread risks:
Teach-back target:
Memory anchors:
```

The central words are not just frequent terms. They are words or phrases that carry the document's meaning, conflict, method, plot, or decision logic.

Infer the reading purpose from the user's request and source type. Use `general quick understanding` when unclear; do not stop to ask unless the purpose would materially change the deliverable. Read `references/purpose-and-modes.md` for purpose profiles and output emphasis.

### Phase 3: Design The Summary Page

Default structure: 4-6 sections, not a full course.

1. **Purpose And Center Words**: the learner's purpose, promised outcome, and the few terms that unlock the document.
2. **Logic Or Storyline**: a because/therefore chain, argument path, process, or narrative arc.
3. **Long Dialogue**: 8-14 short messages between learner, explainer, skeptic, author, practitioner, character, or domain expert.
4. **Misread Risks**: a fixed "do not understand it this way" section with better wording.
5. **Retell Mode**: interactive teach-back workspace with 30-second, 2-minute, and 5-minute retell scaffolds.

Use memory anchors inside the relevant section only when they help the learner remember and retell a center word, storyline turn, contradiction, or misread warning. A visual is never "just a picture"; it must have a named memory job.

For layout and interaction patterns, read `references/page-design.md`.

### Phase 4: Memory Anchors And Optional Xiaohei Images

Treat every visual as a memory anchor. Use Xiaohei-style illustrations only when they help the learner remember a central idea, turn, contradiction, storyline, or misread warning.

- If the user asks for images or specifically asks to use the Xiaohei illustration skill, use the `ian-xiaohei-illustrations` skill if available. Read its `SKILL.md` and relevant references before generating images.
- Before generating an image, define its memory job in one sentence: "This image helps the learner remember..."
- If the user did not explicitly ask to generate images, do not include a visible "Xiaohei", "小黑配图", or "Shot List" section in the page. Use a concept map, timeline, or plain memory-anchor cards instead.
- Do not decorate every section. Choose 1-3 memory anchors for short summaries and 3-5 for long documents.
- Place each generated image next to the section it reinforces, with a short learner-facing caption explaining what to remember.

For visual selection rules, read `references/xiaohei-visuals.md`.

### Phase 5: Build And Review

Build a browser-openable directory using this skill's bundled shell files:

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

Read `references/page-design.md` before building. Copy `styles.css`, `main.js`, `_footer.html`, and `build.sh` from this skill's `references/` directory. Customize `_base.html` from this skill's `references/` directory for the summary title, palette, language, and nav dots.

Final checks:

- The page can be understood in 3-7 minutes.
- The first screen identifies or implies the reading purpose and learner outcome.
- Center words appear near the top.
- Logic/storyline is visible before details.
- Dialogue is long enough to resolve confusion, not just decorative.
- A fixed misread-risk section prevents shallow or wrong summaries.
- The final retell mode helps the learner draft, check, and improve their own explanation without copying wording.
- Important claims were checked against source locators internally, but the final page does not expose page numbers or raw source tags.
- Optional images serve as memory anchors, not decoration, and are generated only after the user asks for them.
- Every visual has a visible learner-facing caption that names what it helps the learner remember.
- Chat controls such as Next Message, Play All, and Reset match the page's visual style; never leave browser-default buttons in the final page.
- Concept diagrams, argument maps, and memory anchors are checked at desktop and narrow widths. If shrinking breaks the visual argument, rearrange it responsively instead of only scaling it down.
- Four peer cards use a balanced two-by-two layout on desktop and tablet, then collapse to one column on small mobile screens. Avoid loose three-plus-one rows.
- Run a reader-copy noise scan: the final `index.html` must not contain implementation notes such as `2x2`, `layout`, `grid`, `style`, `CSS`, `HTML`, `component`, or `fixed` when they refer to the page rather than the document.
- Audit the whole page after each visual/style change, including the first screen, section transitions, diagrams, card grids, chat controls, retell checklist, retell evaluation, and mobile overflow.
- `index.html` opens without a dev server.

## Reference Files

- `references/analysis-and-center-words.md`: how to extract central words, logical/narrative turns, source anchors, and misread risks.
- `references/purpose-and-modes.md`: how to infer reading purpose and adapt summary emphasis.
- `references/page-design.md`: summary page structure, reusable components, long dialogue pattern, and build rules.
- `references/xiaohei-visuals.md`: how to choose memory anchors, when to use Xiaohei images, and how to hand off image generation.
- `references/teach-back.md`: final retell scaffolds, self-checks, and "say it in your own words" patterns.
- `references/styles.css`: bundled page styles; copy verbatim into each generated summary.
- `references/main.js`: bundled interaction runtime; copy verbatim into each generated summary.
- `references/_base.html`: bundled HTML shell; customize only documented placeholders.
- `references/_footer.html`: bundled closing shell; copy verbatim.
- `references/build.sh`: bundled assembly script for `index.html`.
