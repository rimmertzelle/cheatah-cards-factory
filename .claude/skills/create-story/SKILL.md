---
name: create-story
description: Create a swipeable story and cards from lesson materials (7 steps)
argument-hint: "[topic] (optional)"
---

Start the story and cards creation workflow. Follow all 7 steps in order.
If $ARGUMENTS is provided, use it as the lesson topic and skip Step 1.

Before starting, read the following context files:
- `.claude/context/story.md` — story arc, length, tone, and design rules
- `.claude/context/card.md` — card types, anatomy, and writing principles
- `.claude/context/educational.md` — educational principles all content must meet
- `.claude/context/persona.md` — student archetypes (Sanne & Elias)

---

## Step 1 — Ask for the Lesson Topic

Ask the teacher:

> "What is the topic of the lesson these cards are preparing students for?
> Please describe it briefly — including the learning goal and any specific angle
> or question you want students to arrive with in class."

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

Wait for confirmation, then read all files present in `input/`.

---

## Step 3 — Analyse Materials and Extract Story Ingredients

Read all files in `input/` and extract:

**Learning objectives** — What should students understand after this lesson? Infer if not stated.

**Core concepts** — The 2–4 key ideas. Prioritise concepts that are new, counter-intuitive, or often misunderstood.

**Real-world hooks** — Concrete situations or cases that could open the story: surprising data, a decision, a recognisable problem.

**Central tension** — The question or contradiction the student cannot yet resolve. This becomes the cliffhanger.

**Common misconceptions** — Where students typically go wrong. Valuable for tension cards.

**Persona fit** — Note what lands naturally for Sanne (structure, career relevance) vs Elias (theory grounded in practice). Flag anything that risks alienating either archetype.

Summarise findings before moving to Step 4. Do not write the story yet — just show the ingredients.

---

## Step 4 — Create the Story Outline

Using the ingredients from Step 3 and the principles in the context files, create a card-by-card outline.

For each card specify:
- **Card number and type** (Hook / Situation / Tension / Concept / Data / Reflection / Cliffhanger)
- **One-line summary** of what this card does in the story
- **Headline draft** — a first attempt at the card's headline
- **Visual direction** — what kind of image or graphic this card needs

Use the three-act arc:
- **Act 1 — Hook** (1–2 cards): Open with something striking or recognisable
- **Act 2 — Build** (3–6 cards): Develop the tension through a concrete scenario
- **Act 3 — Cliffhanger** (1 card): End on the central lesson question, unresolved

Target 7–10 cards total. Example format:

```text
1. [Hook] — A stat that surprises
   Headline: "68% of new products fail in year one. Most teams saw it coming."
   Visual: Bold typography on a dark background

2. [Situation] — Meet the character
   Headline: "Sara is a product manager. She has 6 weeks to launch."
   Visual: Person at a desk, looking at a screen with a deadline

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

Wait for approval. Apply any requested changes to the outline before continuing.

---

## Step 6 — Write the Full Cards

Using the approved outline and `.claude/context/card.md`, write the full copy for each card:

```markdown
## Card [N] — [Type]

**Headline:** ...

**Body:** ...
*(leave blank if not needed)*

**Prompt:** ...
*(leave blank if not needed)*

**Visual direction:** ...
```

Apply the card writing principles from `card.md`:
- Headline works on its own
- Body is 1–3 sentences maximum, or absent
- Prompt invites, does not test
- Each card readable in 10–15 seconds
- Tone matches the card type

---

## Step 7 — Save Output and Confirm

Create the output folder: `output/<topic-slug>/`

Save the file: `output/<topic-slug>/cards.md`

The file must contain:

1. A brief story header (topic, number of cards, estimated swipe time)
2. All cards in order using the format from Step 6
3. A summary table:

```markdown
## Story Summary

| Card | Type       | Headline (first 6 words...) | Persona focus |
| ---- | ---------- | --------------------------- | ------------- |
| 1    | Hook       | ...                         | Both          |
| 2    | Situation  | ...                         | Sanne         |
```

Confirm with the teacher:

> "All cards are saved in `output/<topic-slug>/cards.md`.
> The story has [N] cards and takes approximately [X] minutes to swipe through.
> Let me know if you'd like to adjust any card before the final version."
