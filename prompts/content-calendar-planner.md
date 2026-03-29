---
type: prompt
id: content-calendar-planner
title: Content Calendar Planner
description: "Creates a structured content calendar for a specified time period"
tags: [Production, planning:editorial, writing:content]
connections:
  - target: content-ideation
    type: derived_from
  - target: audience-analysis
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: task
---

## Purpose

Produces a detailed content calendar that maps topics to publication dates, channels, and responsible parties.

## Prompt

You are a content strategist. Create a content calendar for the specified period based on the topic ideas, audience profile, and business objectives below. For each calendar entry, include:

1. **Publication date** — specific date or week
2. **Content type** — blog post, newsletter, social campaign, video, etc.
3. **Working title** — from the ideation output
4. **Target keyword** — primary SEO target
5. **Channel(s)** — where this will be published and promoted
6. **Status** — planned, briefed, in progress, review, published
7. **Owner** — who is responsible for producing this piece
8. **Notes** — seasonal hooks, dependencies on other content, or coordination needs

### Calendar Principles

- Maintain a consistent publishing cadence (do not front-load or leave gaps)
- Mix content types to keep the audience engaged
- Align with seasonal events, product launches, and industry milestones
- Build topic clusters — group related pieces to strengthen SEO authority
- Leave buffer weeks for reactive content (news, trending topics)

### Inputs

- **Planning period:** Determine an appropriate planning period based on the business objectives and content volume.
- **Topic ideas:** {{steps.generate-content-ideas.output}}
- **Audience profile:** {{steps.profile-audience.output}}
- **Business objectives:** {{input.business_objectives}}
- **Available resources:** Infer from the business context or assume a small content team.
- **Key dates/events:** Identify relevant seasonal events, product launches, and industry milestones from the business context.

## Formatting Rules

- Use British English throughout
- Present the calendar in table format for easy scanning
- Group by week or month depending on the planning period
- Flag any resource conflicts or unrealistic scheduling
