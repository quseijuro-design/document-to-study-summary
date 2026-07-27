---
name: document-to-study-summary
description: "Turn documents, PDFs, DOCX files, Markdown notes, web pages, reports, courses, novels, essays, manuals, or document folders into a concise source-grounded study summary page. Use when someone wants to quickly understand a document, extract central words or themes, connect ideas in a logical or narrative storyline, make a clean visual learning summary, create a longer dialogue-style explanation, optionally generate Xiaohei-style images when explicitly requested, or help the learner retell the document in their own words."
---

# Document To Study Summary

Transform one document, a document set, or an existing generated course into a compact, browser-openable learning summary. The goal is fast understanding and teach-back: after reading the page, the learner should be able to explain the document in their own words.

This skill borrows the page shell and interaction style from `document-to-course`, but compresses the output into a summary-oriented experience: central words, logical storyline, long dialogue, visual anchors, and retell practice.

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
Learner outcome:
Central words:
Logic/storyline:
Key turns:
Characters/actors/roles:
Tensions or tradeoffs:
Misread risks:
Teach-back target:
Suggested visuals:
```

The central words are not just frequent terms. They are words or phrases that carry the document's meaning, conflict, method, plot, or decision logic.

### Phase 3: Design The Summary Page

Default structure: 3-5 sections, not a full course.

1. **Center Words**: the few terms that unlock the document.
2. **Logic Or Storyline**: a because/therefore chain, argument path, process, or narrative arc.
3. **Long Dialogue**: 8-14 short messages between learner, explainer, skeptic, author, practitioner, character, or domain expert.
4. **Visual Anchors**: concept map, timeline, or generated Xiaohei-style images only when explicitly requested.
5. **Teach-Back**: 30-second, 2-minute, and 5-minute retell scaffolds.

For layout and interaction patterns, read `references/page-design.md`.

### Phase 4: Optional Xiaohei Illustrations

Use Xiaohei-style illustrations only when they help the learner remember a central idea, turn, contradiction, or storyline.

- If the user asks for images or specifically asks to use the Xiaohei illustration skill, use the `ian-xiaohei-illustrations` skill if available. Read its `SKILL.md` and relevant references before generating images.
- If the user did not explicitly ask to generate images, do not include a visible "Xiaohei", "小黑配图", or "Shot List" section in the page. Use a concept map, timeline, or plain visual-anchor cards instead.
- Do not decorate every section. Choose 1-3 visual anchors for short summaries and 3-5 for long documents.

For visual selection rules, read `references/xiaohei-visuals.md`.

### Phase 5: Build And Review

Build a browser-openable directory using the `codebase-to-course` shell when present:

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

Read `references/page-design.md` before building. Reuse existing `styles.css` and `main.js`; do not regenerate them unless unavailable.

Final checks:

- The page can be understood in 3-7 minutes.
- Center words appear near the top.
- Logic/storyline is visible before details.
- Dialogue is long enough to resolve confusion, not just decorative.
- The final section helps the learner explain the document without copying wording.
- Important claims were checked against source locators internally, but the final page does not expose page numbers or raw source tags.
- Optional images serve memory, not decoration, and are generated only after the user asks for them.
- Chat controls such as Next Message, Play All, and Reset match the page's visual style; never leave browser-default buttons in the final page.
- `index.html` opens without a dev server.

## Reference Files

- `references/analysis-and-center-words.md`: how to extract central words, logical/narrative turns, source anchors, and misread risks.
- `references/page-design.md`: summary page structure, reusable components, long dialogue pattern, and build rules.
- `references/xiaohei-visuals.md`: when to use Xiaohei illustrations, shot list format, and image-generation handoff.
- `references/teach-back.md`: final retell scaffolds, self-checks, and "say it in your own words" patterns.
