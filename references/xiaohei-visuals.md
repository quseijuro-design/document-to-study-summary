# Xiaohei Visuals

Use this reference when deciding whether to include Xiaohei-style illustrations.

## When To Use

Use Xiaohei visuals for memory anchors, not decoration.

Good targets:

- The central metaphor of the document.
- A before/after shift.
- A contradiction or tradeoff.
- A logic chain that learners confuse.
- A character, role, or actor stuck in a meaningful situation.
- A "do not misread this" warning.

Avoid visuals for:

- Every section equally.
- Purely decorative cover images.
- Long factual lists.
- Places where text is already simpler than the picture.

## Default Output

If the user did not explicitly ask to generate images, provide a shot list inside the summary page:

```text
Visual 1:
placement:
topic:
memory job:
Xiaohei action:
suggested elements:
suggested Chinese labels:
```

Use 1-3 visuals for normal documents. Use 3-5 only for long books, rich essays, or multi-document sets.

## Generating Images

If the user explicitly asks to generate images or "use Xiaohei skill to draw", use the `ian-xiaohei-illustrations` skill if available:

1. Read its `SKILL.md`.
2. Read only the relevant references it names.
3. Generate one image per visual anchor with `image_gen`.
4. Save images under the output directory:

```text
assets/<summary-slug>-illustrations/
```

5. Reference saved images in the summary page with relative paths.

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
