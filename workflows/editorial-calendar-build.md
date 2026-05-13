---
type: workflow
id: editorial-calendar-build
title: Editorial Calendar Build
description: "Audience analysis, ideation, calendar planning, and brief creation for editorial planning"
tags: [Production, Audience, Content]
connections:
  - target: audience-analysis
    type: uses
  - target: content-ideation
    type: uses
  - target: content-briefing
    type: uses
  - target: language-polish
    type: uses
  - target: llm-service
    type: runs_on
  - target: editorial-calendar-template
    type: references
metadata:
  estimated_duration: "15-30 minutes"
  trigger: manual
output_step: "language-polish"
composite_steps:
  - "audience-analysis"
  - "content-ideation"
  - "content-briefing"
  - "language-polish"
execution:
  - skill: "audience-analysis"
    prompt: "content-calendar-planner"
    step_type: "synthesis"
  - skill: "content-ideation"
    step_type: "generation"
    prompt: "generate-content-ideas"
    context:
      content_context: "No additional context"
  - skill: "content-briefing"
    prompt: "create-content-brief"
    step_type: "generation"
    context:
      target_audience: "General professional audience"
  - skill: "language-polish"
    prompt: "polish-language"
    step_type: "content"
    context:
      voice_profile: "Neutral professional tone"
      grammar_strictness: "Professional"
---

## Overview

This workflow builds a complete editorial calendar from audience analysis through to individual content briefs. It produces a strategic content plan that aligns topics with audience needs, business objectives, and seasonal opportunities.

## Pipeline Stages

### Stage 1: Audience Analysis

**Input:** Industry/niche, existing audience data, competitor analysis, business objectives

Invoke the **audience-analysis** skill via the **profile-audience** prompt to produce a detailed audience profile. This profile informs all subsequent stages.

**Output:** Audience profile with demographics, pain points, content preferences, and gap analysis.

### Stage 2: Content Ideation

**Input:** Audience profile from Stage 1, seed keywords, existing content inventory

Invoke the **content-ideation** skill via the **generate-content-ideas** prompt to produce a ranked list of topic ideas tailored to the audience profile.

**Output:** Ranked topic ideas with titles, angles, and keyword targets.

### Stage 3: Calendar Planning

**Input:** Topic ideas from Stage 2, planning period, key dates, available resources

Invoke the **content-calendar-planner** prompt to map topics to publication dates, channels, and owners. The calendar should maintain a consistent cadence and align with seasonal opportunities.

**Output:** Structured editorial calendar for the planning period.

### Stage 4: Brief Creation

**Input:** Calendar entries from Stage 3, audience profile from Stage 1

For each content piece in the calendar, invoke the **content-briefing** skill via the **create-content-brief** prompt to produce a detailed writer brief.

**Output:** Individual content briefs for each calendar entry, ready for assignment.

## Error Handling

- If audience data is insufficient, produce a hypothesis-based profile and flag assumptions for validation
- If ideation produces fewer than 10 viable topics, broaden the keyword set or extend the niche scope
- If the calendar has resource conflicts, flag them and suggest alternative scheduling
- If briefs are produced before the calendar is finalised, they may need updating — note this dependency

## Inputs

| Name | Required | Description | Example |
|------|----------|-------------|---------|
| `{{input.industry_niche}}` | Yes | Industry/niche | `Paste the relevant brief, notes, source material, or dataset here.` |
| `{{input.existing_audience_data}}` | Yes | existing audience data | `Paste the latest metrics, exported data, or summary notes relevant to the workflow.` |
| `{{input.competitor_analysis}}` | Yes | competitor analysis | `Paste the relevant brief, notes, source material, or dataset here.` |
| `{{input.business_objectives}}` | No | business objectives | `Paste the relevant brief, notes, source material, or dataset here.` |

## Outputs

| Name | Description |
|------|-------------|
| Audience profile | Audience profile with demographics, pain points, content preferences, and gap analysis |
| Ranked topic ideas | Ranked topic ideas with titles, angles, and keyword targets |
| Structured editorial calendar for the planning period | Structured editorial calendar for the planning period |
| Individual content briefs for each calendar entry, ready for assignment | Individual content briefs for each calendar entry, ready for assignment |

## Setup

Before running this workflow:

1. No external services required — paste your content directly and provide any supporting context as inputs or source nodes.
2. Review the included documents, assets, or source nodes and customise them to match your team, brand, or domain conventions where needed.
3. No specific AI provider or API key is required beyond your configured skrptiq LLM provider.

## Provider Notes

- Most stages work with any capable model; stronger models usually improve synthesis, judgement, and writing quality.
- Extraction, classification, and formatting steps generally run well on smaller or faster models.
- Because there are no vendor-specific integrations here, provider choice is mostly a trade-off between speed, quality, and cost.

## Example Input

To test this workflow immediately after import:

```
Industry Niche: "Paste the relevant brief, notes, source material, or dataset here."
Existing Audience Data: "Paste the latest metrics, exported data, or summary notes relevant to the workflow."
Competitor Analysis: "Paste the relevant brief, notes, source material, or dataset here."
Business Objectives: "Paste the relevant brief, notes, source material, or dataset here."
```

