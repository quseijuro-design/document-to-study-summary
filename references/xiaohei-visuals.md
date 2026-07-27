# Xiaohei Memory Anchors

Use this reference when deciding whether to include Xiaohei-style illustrations or other visual memory anchors.

## Core Principle

Images are memory anchors, not illustrations. A useful image lets the learner remember and retell one specific idea after leaving the page.

Every visual must answer:

```text
What should the learner remember because this image exists?
Which center word, storyline turn, contradiction, or misread risk does it anchor?
Where should it appear in the page so it reinforces that idea?
What sentence should the learner be able to say after seeing it?
```

If those answers are weak, do not generate an image.

## When To Use

Use Xiaohei visuals for memory anchors, not decoration.

Good memory-anchor targets:

- The central metaphor of the document.
- A before/after shift.
- A contradiction or tradeoff.
- A logic chain that learners confuse.
- A character, role, or actor stuck in a meaningful situation.
- A "do not misread this" warning.
- A retell sentence that is hard to remember without a metaphor.

Avoid visuals for:

- Every section equally.
- Purely decorative cover images.
- Long factual lists.
- Places where text is already simpler than the picture.
- A generic title image or mood-setting cover.
- A character portrait that does not encode a conflict or turn.

## Default Output

If the user did not explicitly ask to generate images, do not include a visible Xiaohei section or shot list in the summary page. Use neutral learner-facing memory anchors instead, such as:

- a concept map
- a timeline
- a before/after comparison
- a key-turn card row
- a "remember this as..." metaphor card

You may keep an internal planning note like this while building, but do not render it as a shot list in the page:

```text
Visual 1:
placement:
center word / storyline turn / misread risk:
memory job:
retell sentence:
Xiaohei action:
suggested elements:
suggested Chinese labels:
```

Use 1-3 memory anchors for normal documents. Use 3-5 only for long books, rich essays, or multi-document sets.

## Generating Images

If the user explicitly asks to generate images, asks to use Xiaohei, or says "use Xiaohei skill to draw", use the `ian-xiaohei-illustrations` skill if available:

1. Read its `SKILL.md`.
2. Read only the relevant references it names.
3. Generate one image per memory anchor with `image_gen`.
4. Save images under the output directory:

```text
assets/<summary-slug>-illustrations/
```

5. Reference saved images in the summary page with relative paths.
6. Put each image near the section it anchors, not in a separate gallery.
7. Add a short caption:

```text
记住这个画面：...
它帮你复述：...
```

Do not leave prompt text or a shot list as a substitute for images when the user asked to generate images.

## Page Placement

Place memory anchors where they do learning work:

- Center word anchor: next to the center-word cards or word map.
- Storyline anchor: inside the logic/storyline module near the relevant turn.
- Misread anchor: inside the misread-risk section beside the warning.
- Retell anchor: near the retell mode as a "remember this picture when speaking" cue.

Never put all images into a final "images" section unless the user explicitly asks for an image gallery.

## Prompt Requirements

Each image prompt should preserve the Xiaohei style:

- 16:9 Chinese article illustration.
- Clean white background.
- Black hand-drawn linework.
- Xiaohei as the main actor, not decoration.
- Sparse red/orange/blue handwritten Chinese annotations.
- Lots of whitespace.
- One central visual metaphor only.
- Avoid PPT, commercial illustration, cute cartoon, dense system diagram, or a large title in the top-left corner.

## Quality Check

Reject or regenerate if:

- Xiaohei is only standing beside the idea.
- The visual is a literal flowchart with no metaphor.
- There is too much text.
- The Chinese text is garbled or excessive.
- The image feels like a cover poster instead of an article-side explanation.
- The picture explains the wrong center word.
- The image could be removed without weakening memory or retelling.
