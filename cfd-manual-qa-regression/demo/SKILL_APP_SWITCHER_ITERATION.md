---
name: app-switcher-manual-qa-iteration
description: 'Iterative manual QA skill for the app-switcher feature. Use when a requirement document and UI design are available, and the goal is to generate test cases while learning and updating a shared app profile for the next iteration.'
argument-hint: 'Requirement source, UI source, app profile, and target release'
user-invocable: true
disable-model-invocation: false
---

# App Switcher Manual QA Iteration Skill

## Purpose
- Generate test cases from the current requirement and UI design.
- Capture newly learned app behavior into a shared app profile.
- Emit a Skill Delta so the next iteration gets better.

## Required Inputs
- Requirement document content or readable extract.
- UI design content or readable extract.
- Current app profile.
- Build/version and environment.

## Working Rule
1. Read the requirement and UI design.
2. Extract confirmed behavior only.
3. Update the app profile with confirmed facts, risks, and terminology.
4. Generate test cases with explicit verify steps.
5. Produce a Skill Delta containing new knowledge, gaps, and follow-up questions.

## Output Sections
1. Scope and assumptions
2. App behavior learned from the sources
3. Test cases
4. Coverage gaps
5. App profile delta
6. Skill Delta for next iteration
