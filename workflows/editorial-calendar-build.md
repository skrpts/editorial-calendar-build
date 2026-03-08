---
type: workflow
id: editorial-calendar-build
title: Editorial Calendar Build
description: "Audience analysis, ideation, calendar planning, and brief creation for editorial planning"
tags: [Draft]
connections:
  - target: audience-analysis
    type: uses
  - target: content-ideation
    type: uses
  - target: content-briefing
    type: uses
  - target: profile-audience
    type: uses
  - target: generate-content-ideas
    type: uses
  - target: content-calendar-planner
    type: uses
  - target: create-content-brief
    type: uses
  - target: anthropic-claude
    type: runs_on
  - target: openai-gpt4
    type: runs_on
metadata:
  estimated_duration: "15-30 minutes"
  trigger: manual
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
