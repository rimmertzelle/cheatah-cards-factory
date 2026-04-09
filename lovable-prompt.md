# Lovable Prompt — Cheatah Cards

Build a web app called "Cheatah Cards" — a learning tool that works like Instagram Stories, but for education. It has two sides: a teacher interface for creating story cards, and a student interface for swiping through them.

---

## Core concept

A "story" is a swipeable sequence of 7–10 cards that prepares students for an upcoming class lesson. Each card has one idea, one visual, one headline. Together they follow a three-act arc: Hook → Build → Cliffhanger. The cliffhanger ends the story without resolving the central question — the lesson does that.

After reading each card, the student makes a self-assessment (not a quiz):
- "I already know this" → captured on cheatsheet with low priority
- "I really don't care" → captured, flagged as low relevance
- "I don't know" → captured with high priority and more depth

Every card ends up on the cheatsheet. The action determines depth and order, not whether it appears.

---

## Teacher interface

### Create story flow (multi-step wizard)
1. Enter lesson topic and learning goal (text input)
2. Upload lesson materials (PDF, PPTX, DOCX, or plain text) — multiple files supported
3. Claude analyses the materials and returns structured "story ingredients":
   - Learning objectives
   - Core concepts (2–4)
   - Real-world hooks
   - Central tension
   - Common misconceptions
4. Claude generates a story outline: card-by-card with type, headline draft, and visual direction
5. Teacher reviews and edits the outline (each card editable inline)
6. Teacher approves → Claude writes full card copy
7. Teacher reviews final cards (each editable), then publishes

### Card types (displayed with a type badge)
Hook · Situation · Tension · Concept · Data · Reflection · Cliffhanger

### Each card has
- Type (badge)
- Headline (bold, large)
- Body (optional, 1–3 sentences)
- Prompt (optional, shown as a question)
- Visual direction (text description shown to teacher; in a future version this becomes an actual image)

### Teacher dashboard
- List of all created stories
- Status per story: Draft / Published / Archived
- Link to share the story with students (simple shareable URL or code)

---

## Student interface

### Story viewer
- Full-screen swipeable card view (one card at a time)
- Swipe left/right or tap arrows to navigate
- Progress indicator at the top (e.g. 3 / 8)
- Each card shows: visual area (placeholder image or colour block based on mood), headline, optional body, optional prompt

### Self-assessment (after each card)
Three large tap targets at the bottom of each card:
- "I already know this" (light/neutral style)
- "I really don't care" (light/neutral style)
- "I don't know" (light/neutral style)

Student must tap one to advance to the next card.

### Cheatsheet (shown after the last card)
Auto-generated summary of all cards:
- "I don't know" items listed first, with headline + body
- "I already know this" items listed below, headline only
- "I really don't care" items at the bottom, headline only with a flag
- Option to download as PDF or copy as text

---

## Design
- Clean, minimal UI — similar to an Instagram or LinkedIn story
- Cards use a large headline (think: poster typography), small body
- Card background colour per type:
  - Hook: dark/charcoal
  - Situation: warm neutral
  - Tension: muted orange or amber
  - Concept: deep blue
  - Data: clean white with bold number
  - Reflection: soft grey-green
  - Cliffhanger: dark with forward-looking feel
- Mobile-first but desktop-readable
- No gamification, no scores — this is metacognition, not a quiz

---

## Tech notes
- Use Claude API (claude-sonnet-4-6) for the story and card generation
- Teacher flow uses streaming responses where possible (show generation progress)
- Store stories and card data in Supabase
- Auth: teacher login (email/password), students access via shareable link (no login required)
- Student responses (self-assessments) stored per session (anonymous or linked to student ID if provided)
