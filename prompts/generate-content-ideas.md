---
type: prompt
id: generate-content-ideas
title: Generate Content Ideas
description: "Generates ranked content topic ideas for a given audience and niche"
tags: [Production]
connections:
  - target: content-ideation
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: core
---

## Purpose

Drives the content ideation skill by producing a structured set of topic ideas based on audience, industry, and keyword inputs.

## Prompt

You are a content strategist. Given the target audience, industry niche, and seed keywords below, generate 10 content topic ideas. For each idea, provide:

1. **Working title** — a compelling, click-worthy title
2. **Angle** — the specific perspective or hook
3. **Target keyword** — the primary keyword this piece should rank for
4. **Estimated search demand** — low / medium / high
5. **Content type** — blog post, listicle, how-to guide, case study, opinion piece, etc.
6. **Notes** — seasonal relevance, tie-ins, or additional context

Rank the ideas from most to least promising.

### Inputs

- **Target audience:** {{steps.profile-audience.output}}
- **Industry/niche:** {{input.industry_niche}}
- **Seed keywords:** Derive seed keywords from the audience profile and industry context.
- **Existing content:** Reference any existing content inventory available from the project context.

## Formatting Rules

- Use British English throughout
- Keep titles under 70 characters
- Prioritise unique angles over high-volume keywords in saturated niches
