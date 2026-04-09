# Story & Cards Creation Workflow

This file defines the step-by-step workflow for creating a story and its cards from lesson materials. Always follow these steps in order.

---

## Workflow Overview

```text
Step 1 → Ask for the lesson topic
Step 2 → Ask teacher to add materials to the input folder
Step 3 → Analyse the materials and extract story ingredients
Step 4 → Create the story outline (arc + card plan)
Step 5 → Ask teacher to review and approve the story outline
Step 6 → Write the full cards in markdown
Step 7 → Save output and confirm with teacher
```

---

## Step 1 — Ask for the Lesson Topic

Ask the teacher:

> "What is the topic of the lesson these cards are preparing students for?
> Please describe it briefly — including the learning goal and any specific angle or question you want students to arrive with in class."

Wait for the answer before proceeding.

---

## Step 2 — Ask Teacher to Add Materials

Ask the teacher:

> "Please add the lesson materials to the `input/` folder in this project.
> This can include:
>
> - Lecture slides (PDF, PPTX, or exported markdown)
> - Reading materials or articles
> - Case studies or exercises
> - Your own notes or a lesson outline
>
> Let me know when the files are in the folder and I will start the analysis."

Wait for confirmation before proceeding. Then read all files present in `input/`.

---

## Step 3 — Analyse Materials and Extract Story Ingredients

Read all files in `input/` and extract the following:

**Learning objectives**
What should students understand or be able to do after this lesson? If not stated explicitly, infer from the content.

**Core concepts**
The 2–4 key ideas the lesson introduces. Prioritise concepts that are new, counter-intuitive, or often misunderstood.

**Real-world hooks**
Concrete situations, examples, or cases from the materials that could serve as the opening of a story. Look for: surprising data, a decision someone had to make, a recognisable problem.

**Central tension**
The question or contradiction at the heart of the lesson — the thing the student does not yet know how to resolve. This will become the cliffhanger.

**Common misconceptions**
Any points in the materials where students tend to go wrong or bring the wrong prior knowledge. These are valuable for the tension cards.

**Persona fit**
Note which elements of the materials will land naturally for Sanne (needs structure and career relevance) versus Elias (experienced, needs theory connected to practice). Flag any content that risks alienating either archetype.

Summarise your findings in a brief analysis before moving to Step 4. Do not yet write the story — just show the ingredients you found.

---

## Step 4 — Create the Story Outline

Using the ingredients from Step 3 and the principles in `.claude/context/story.md`, `.claude/context/educational.md`, and `.claude/context/persona.md`, create a story outline.

The outline lists each card in order, without writing the full copy yet. For each card, specify:

- **Card number and type** (Hook / Situation / Tension / Concept / Data / Reflection / Cliffhanger)
- **One-line summary** of what this card does in the story
- **Headline draft** — a first attempt at the card's headline
- **Visual direction** — what kind of image or graphic this card needs

Use the three-act arc from `story.md`:

- **Act 1 — Hook** (1–2 cards): Open with something striking or recognisable
- **Act 2 — Build** (3–6 cards): Develop the tension through a concrete scenario
- **Act 3 — Cliffhanger** (1 card): End on the central lesson question, unresolved

Target 7–10 cards total for a standard pre-class story.

Present the outline as a numbered list. Example format:

```text
1. [Hook] — A stat that surprises
   Headline: "68% of new products fail in year one. Most teams saw it coming."
   Visual: Bold typography on a dark background

2. [Situation] — Meet the character
   Headline: "Sara is a product manager. She has 6 weeks to launch."
   Visual: Person at a desk, looking at a screen with a deadline

...

8. [Cliffhanger] — The lesson question
   Headline: "So — how do you know when to stop and pivot?"
   Visual: A fork in the road, minimalist illustration
```

---

## Step 5 — Ask Teacher to Review the Story Outline

Present the outline and ask:

> "Here is the story outline for *[topic]*. Each card is listed with its type, headline draft, and visual direction.
>
> Before I write the full card copy, please check:
>
> - Does the story arc feel right? Does it build toward the lesson question?
> - Are the right concepts included — and nothing important missing?
> - Does the opening feel engaging for your students?
> - Any headlines or cards you'd like to change?
>
> Let me know what to adjust, or confirm to proceed."

Wait for approval before continuing. Apply any requested changes to the outline first, then proceed.

---

## Step 6 — Write the Full Cards

Using the approved outline and the principles in `.claude/context/card.md`, write the full copy for each card.

For each card, produce:

```markdown
## Card [N] — [Type]

**Headline:** ...

**Body:** ...
*(leave blank if not needed)*

**Prompt:** ...
*(leave blank if not needed)*

**Visual direction:** ...
```

Apply the card writing principles:

- Headline works on its own — if a student only sees this, they still take something away
- Body is 1–3 sentences maximum, or absent
- Prompt invites, does not test
- Each card readable in 10–15 seconds
- Tone matches the card type (see tone table in `card.md`)

---

## Step 7 — Save Output and Confirm

Create the output folder: `output/<topic-slug>/`

Save the file: `output/<topic-slug>/cards.md`

The file should contain:

1. A brief story header (topic, number of cards, estimated swipe time)
2. All cards in order, using the format from Step 6
3. A summary table at the end

Summary table format:

```markdown
## Story Summary

| Card | Type        | Headline (first 6 words...)  | Persona focus |
| ---- | ----------- | ---------------------------- | ------------- |
| 1    | Hook        | ...                          | Both          |
| 2    | Situation   | ...                          | Sanne         |
| ...  | ...         | ...                          | ...           |
```

Confirm with the teacher:

> "All cards are saved in `output/<topic-slug>/cards.md`.
>
> The story has [N] cards and takes approximately [X] minutes to swipe through.
>
> Let me know if you'd like to adjust any card before the final version."

---

## Context Files (Reference)

All story and card content should reflect the principles in the following files:

| File                              | Purpose                                      |
| --------------------------------- | -------------------------------------------- |
| `.claude/context/story.md`        | Story arc, length, tone, and design rules    |
| `.claude/context/card.md`         | Card types, anatomy, writing principles      |
| `.claude/context/educational.md`  | Educational principles all content must meet |
| `.claude/context/persona.md`      | Student archetypes to design for             |
