# Lovable Prompt — Cheatah Cards

Build a web app called "Cheatah Cards" — a learning tool that works like Instagram Stories, but for education. It has two sides: a teacher interface for creating story cards and a reference cheatsheet, and a student interface for swiping through the story and reviewing their personal cheatsheet.

---

## Core concept

A "story" is a swipeable sequence of 7–10 cards that prepares students for an upcoming class lesson. Each card has one idea, one visual, one headline. Together they follow a three-act arc: Hook → Build → Cliffhanger. The cliffhanger ends the story without resolving the central question — the lesson does that.

After reading each card, the student makes a self-assessment (not a quiz):

- "I already know this" → captured on their personal cheatsheet with low priority
- "I really don't care" → captured, flagged as low relevance
- "I don't know" → captured with high priority and more detail

Every card ends up on the personal cheatsheet. The action determines depth and order, not whether it appears.

In addition to the story, the teacher publishes a **reference cheatsheet** — a layered document covering all lesson concepts at three knowledge levels. Students can access this before or after the lesson.

---

## Teacher interface

### Create story flow (multi-step wizard)

**Step 1 — Topic**
Text input: lesson topic and learning goal.

**Step 2 — Upload materials**
Upload lesson materials (PDF, PPTX, DOCX, or plain text). Multiple files supported.

**Step 3 — Analysis**
Claude analyses the materials and displays structured story ingredients:

- Learning objectives
- Core concepts (2–4)
- Real-world hooks
- Central tension
- Common misconceptions

Teacher can review before proceeding.

**Step 4 — Story outline**
Claude generates a card-by-card outline with type, headline draft, and visual direction. Teacher can edit each card inline before approving.

**Step 5 — Full card copy**
Claude writes the complete copy for each card. Teacher reviews and edits, then publishes the story.

**Step 6 — Reference cheatsheet**
Claude generates a layered reference cheatsheet from the uploaded materials (not just the cards). Teacher reviews and publishes alongside the story.

### Card types (displayed with a type badge)

Hook · Situation · Tension · Concept · Data · Reflection · Cliffhanger

### Each card has

- Type (badge)
- Headline (bold, large)
- Body (optional, 1–3 sentences)
- Prompt (optional, shown as a soft question)
- Visual direction (text description; placeholder image in v1)

### Teacher dashboard

- List of all created stories with status: Draft / Published / Archived
- Each story shows: title, card count, estimated swipe time, publish date
- Shareable student link per story (no login required for students)

---

## Reference cheatsheet

The reference cheatsheet is generated from the full lesson materials — not just the story cards. It covers all key concepts at three levels of detail, designed to fit on a single A4 page.

### Three layers

**Novice** — for students new to this topic
Full definitions with context sentences and a brief example per concept. This layer takes roughly half the page.

**Mediate** — for students with some prior knowledge
Key terms with one-sentence definitions. No examples. Takes roughly one third of the page.

**Expert** — for students who already know the topic
Terms with a 5–10 word reminder only. A quick scan before class. Takes the remaining strip.

### Cheatsheet design

- Three clearly labelled sections on one page: Novice / Mediate / Expert
- Same concepts appear in all three layers — only the depth changes
- Clean layout: bold concept names, short text blocks, clear dividers between layers
- Printable and readable on screen
- Teacher can edit any layer before publishing

---

## Student interface

### Story viewer

- Full-screen swipeable card view, one card at a time
- Swipe left/right or tap arrows to navigate
- Progress bar at the top (e.g. card 3 of 8)
- Each card shows: colour block or placeholder image (mood-matched per card type), headline, optional body, optional prompt

### Self-assessment

Shown after each card. Three large tap targets at the bottom:

- "I already know this"
- "I really don't care"
- "I don't know"

Student must tap one to advance. No skipping.

### Personal cheatsheet

Shown after the last card. Auto-generated from the student's self-assessments:

- "I don't know" items first — headline + full body text
- "I already know this" items next — headline only
- "I really don't care" items last — headline only, with a small flag icon

Option to download as PDF or copy as plain text.

### Reference cheatsheet tab

The teacher-published layered cheatsheet. Student can select which layer to read (Novice / Mediate / Expert) using a toggle. Printable.

---

## Card design

- Clean, minimal UI — similar to an Instagram or LinkedIn story
- Cards use large headline typography, small supporting body text
- Card background colour per type:

  | Card type   | Background colour             |
  | ----------- | ----------------------------- |
  | Hook        | Dark/charcoal                 |
  | Situation   | Warm neutral                  |
  | Tension     | Muted orange or amber         |
  | Concept     | Deep blue                     |
  | Data        | Clean white, bold number      |
  | Reflection  | Soft grey-green               |
  | Cliffhanger | Dark, forward-looking feel    |

- Mobile-first, desktop-readable
- No gamification, no scores — this is metacognition, not a quiz

---

## Tech notes

- Use Claude API (model: claude-sonnet-4-6) for story generation, card copy, and cheatsheet generation
- Use streaming responses in the teacher wizard to show progress during generation
- Store stories, cards, and cheatsheet data in Supabase
- Auth: teacher login via email/password; students access via a shareable link with no login required
- Student self-assessment responses stored per session; optionally linked to a student name or ID if entered
- Reference cheatsheet stored as structured data (per concept, per layer) so it can be rendered responsively and toggled by layer
