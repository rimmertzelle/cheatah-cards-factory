# Cheatah Cards Factory

This project generates swipeable story cards that prepare students for class.
Teachers provide lesson materials; Claude produces a narrative card story students can swipe through before the lesson.

## How to use

Run `/create-story` to start the full 7-step workflow.
The workflow is defined in `.claude/skills/create-story/SKILL.md`.

## Folders

- `input/` — drop lesson materials here before running the workflow
- `output/<topic-slug>/` — generated cards are saved here

## Context files

Always read these before generating story or card content:

| File                             | Purpose                                             |
| -------------------------------- | --------------------------------------------------- |
| `.claude/context/story.md`       | Story arc, length, tone, and design rules           |
| `.claude/context/card.md`        | Card types, anatomy, and writing principles         |
| `.claude/context/educational.md` | Educational principles all content must meet        |
| `.claude/context/persona.md`     | Student archetypes: Sanne (HAVO) & Elias (MBO/work) |

## Student archetypes

**Sanne** (19, HAVO) — needs structure, career relevance, worked examples before open tasks.
**Elias** (24, MBO + work experience) — needs theory grounded in practice; responds when his experience is respected.

Every story and every card should be legible and engaging for both archetypes.
