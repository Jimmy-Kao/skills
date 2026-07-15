---
name: kline-phase1-manual-qa-iteration
description: 'Iterative manual QA skill for K-line phase 1 trading-chart features. Use when a requirement document and UI design are available, and the goal is to generate chart-related test cases while learning and updating a shared app profile for the next iteration.'
argument-hint: 'Requirement source, UI source, app profile, and target release'
user-invocable: true
disable-model-invocation: false
---

# K-Line Phase 1 Manual QA Iteration Skill

## Purpose
- Generate a reusable iterative skill from a requirement document.
- Generate Google Sheets-ready test cases from a requirement document, with optional UI input when available.
- Capture newly learned app behavior so the next iteration is more accurate.

## Required Inputs
- Requirement document content or readable extract.

## Optional Inputs
- UI design content or readable extract.
- Current app profile if already available.
- Build/version and environment if already known.

## Working Rule
1. Read the requirement document first.
2. Read the UI only if it is provided.
3. Extract confirmed behavior only and separate it from assumptions.
4. Generate Google Sheets-ready test cases.
5. Generate the iterative skill content for the next round.
6. Capture only the new knowledge needed to improve the next run.

## Minimal Workflow
Use this exact flow and nothing extra:
1. User provides the requirement document.
2. User optionally provides UI.
3. Produce the test cases.
4. Produce the iterative skill update for the next round.

Do not add extra user-facing review steps, approvals, or intermediate checklists unless the requirement itself is ambiguous.

## Skill Delta Content
The Skill Delta must capture:
- Confirmed app behavior learned this round
- Default states and visibility rules learned this round
- Negative and boundary conditions learned this round
- Gaps that still need confirmation
- Exact wording or labels that should be reused later
- Notes for the next iteration so the skill becomes more accurate

## Iteration Contract
When the user supplies a requirement document, do all of the following:
1. Distill the app behavior, user roles, screens, workflows, validations, and boundary rules from the document.
2. Produce test cases that reflect the requirement document and any provided UI.
3. Emit a Skill Delta section that can be merged into the next revision of this skill.

## Output Sections
1. Scope and assumptions
2. Risk-ranked test plan
3. Google Sheets-ready test case table
4. Iterative skill update for the next round

The user-facing output must stay focused on only the test cases and the skill update. Internal app-profile learning can be retained as working memory, but it should not introduce extra user workflow steps.

## Team Usage Rule
- Team members should always use the same shared skill folder and the same Google Sheets table format.
- If UI is available, use it; if not, proceed with the requirement document alone.
- Do not overwrite confirmed facts with assumptions.
