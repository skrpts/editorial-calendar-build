---
type: prompt
id: create-content-brief
title: Create Content Brief
description: "Creates a structured content brief for a writer or content producer"
tags: [Production]
connections:
  - target: content-briefing
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: core
---

## Purpose

Drives the content briefing skill by producing a detailed brief that a writer can follow to create content matching the required standard.

## Prompt

You are a content strategist. Create a detailed content brief for a writer based on the inputs below. The brief should include:

1. **Working title** — a compelling title that incorporates the target keyword
2. **Angle/hook** — the specific perspective that makes this piece unique
3. **Target audience** — who this is for and what they care about
4. **Outline** — detailed structure with H2 and H3 headings
5. **SEO targets** — primary and secondary keywords
6. **Tone and style** — voice, formality level, and style rules
7. **Length** — target word count
8. **Call to action** — what the reader should do after reading

### Inputs

- **Topic:** Using a calendar entry from the previous stage.
- **Target keyword(s):** Using the keyword targets assigned in the editorial calendar.
- **Audience persona:** Using the audience profile produced in Stage 1.
- **Desired length:** Determine based on the content type and topic depth.
- **Reference URLs:** Include any relevant references from the research stages.

## Formatting Rules

- Use British English throughout
- Keep the brief actionable
- Include specific examples where possible
