# Analysis And Center Words

Use this reference during source extraction and synthesis.

## Source Manifest

Track each source with a stable id:

```text
- id: S1
  path/url: ...
  title: ...
  type: pdf | docx | md | html | course | folder | other
  locators: pages | headings | modules | sections | URLs
  scope: what this source appears to cover
```

Use locators internally to keep the summary grounded and to verify claims. Do not display raw locator strings in the final learner page. Avoid visible labels such as `S1`, `Source:`, `metadata`, `p. 12`, or `pp. 8-25`.

When the learner needs confidence without technical labels, fold provenance into natural language:

```text
The early progress-report entries show...
The middle chapters shift toward...
The policy definition section narrows...
```

## Extract Center Words

Center words are the terms that make the document teachable. Do not rely on frequency alone.

Prefer words that satisfy at least two of these:

- The document defines or repeatedly reframes the term.
- The term links multiple sections, chapters, characters, claims, or decisions.
- The term marks a before/after shift.
- The term carries a conflict, tradeoff, or value judgment.
- The term is easy for learners to misuse.
- The term is a compact handle for retelling the document.

For each center word capture:

```text
word:
plain meaning:
internal source locator:
why it matters:
connected words:
common misread:
```

Use 5-9 center words by default. Use 3-5 for short documents and 9-12 only for dense books or document sets.

## Build Logic Or Storyline

Choose the structure that fits the source:

- Essay/report: problem -> claim -> evidence -> implication -> caveat.
- Manual/process: goal -> prerequisites -> steps -> failure modes -> done state.
- Policy/contract: scope -> definitions -> obligations -> exceptions -> escalation.
- Novel/memoir/narrative: setup -> desire -> change -> cost -> recognition.
- Course: learning promise -> modules -> repeated patterns -> final capability.

Write the logic as a chain:

```text
Because ...
Therefore ...
But ...
So ...
Finally ...
```

For narratives, preserve chronology only where chronology teaches meaning. Avoid full plot reconstruction for copyrighted long-form works.

## Identify Key Turns

Key turns are points where the reader's understanding should change.

Look for:

- A new definition that changes earlier assumptions.
- A role or relationship reversal.
- A contradiction or caveat.
- A cause/effect chain becoming visible.
- A cost that complicates a benefit.
- A concrete example that makes the abstract claim usable.

Each final summary should include 3-6 key turns.

## Misread Risks

Include a short "Do not misread this as..." section when useful.

Good misread warnings:

- Not "X is good/bad"; rather "X creates tradeoff Y."
- Not "the document proves X"; rather "the document argues X under condition Y."
- Not "this character/role is simply wrong"; rather "this role reveals tension Y."
- Not "the process is linear"; rather "step N loops back when condition Y fails."

## Internal Analysis Output

Before writing the page, create a private map:

```text
One-sentence thesis:
Learner should be able to say:
Center words:
Storyline:
Key turns:
Best short source anchors, for internal checking only:
Long dialogue roles:
Visual anchors:
Teach-back scaffold:
```
