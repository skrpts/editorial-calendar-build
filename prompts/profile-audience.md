---
type: prompt
id: profile-audience
title: Profile Audience
description: "Creates a detailed audience profile from available data and market context"
tags: []
connections:
  - target: audience-analysis
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: core
---

## Purpose

Drives the audience analysis skill by producing a structured audience profile that informs content strategy.

## Prompt

You are a market research analyst. Using the data and context below, create a detailed audience profile. Cover:

1. **Demographics** — age range, job titles/roles, industry, company size, geography
2. **Psychographics** — values, motivations, frustrations, aspirations
3. **Content consumption** — preferred formats (blog, video, podcast, newsletter), frequency, platforms, time of day
4. **Knowledge level** — beginner, intermediate, or expert in the subject matter
5. **Pain points** — the top 3-5 problems this audience faces that content could address
6. **Content gaps** — topics or formats that competitors are not covering well
7. **Decision drivers** — what influences this audience's choices (data, peer recommendations, case studies, etc.)

### Inputs

- **Industry/niche:** {niche}
- **Existing audience data:** {data}
- **Competitor analysis:** {competitors}
- **Business objectives:** {objectives}

## Formatting Rules

- Use British English throughout
- Be specific — "marketing managers at B2B SaaS companies with 50-200 employees" is better than "marketers"
- Distinguish between confirmed data and inferred characteristics
- Prioritise actionable insights over comprehensive coverage
