---
name: cfd-manual-qa-regression
description: 'Manual QA workflow for Contract for Difference (CFD) trading product releases: test planning, risk-based positive and negative test case design, full manual regression execution with efficiency tactics, release sign-off readiness, and coverage tracking. Use when preparing or executing manual test cycles and reducing repetitive regression effort.'
argument-hint: 'Feature or release scope to test, risk areas, and timeline'
user-invocable: true
disable-model-invocation: false
---

# CFD Manual QA Regression

## What This Skill Produces
- A focused manual test plan for the release scope
- Positive and negative test cases prioritized by risk
- A regression set split into must-run and conditional cases
- Coverage tracking against requirements and risk areas
- A clear sign-off recommendation with blockers and residual risks

## When to Use
- Planning manual QA for a new CFD feature or release
- Building or refining test cases for critical trading flows (order lifecycle, pricing, P&L, margin, risk controls)
- Running regression under time constraints
- Preparing go or no-go QA sign-off before release

## Inputs To Request
- Release scope and changed components
- Requirements, acceptance criteria, and known risks
- Environments, build details, and test data availability
- Timeline and execution capacity
- Severity definitions and release gate criteria

## Mandatory Inputs Contract
- Required:
   - Release scope, impacted modules, and in-scope/out-of-scope boundaries
   - Acceptance criteria per requirement
   - Build version, environment, and data readiness
   - Defect severity policy for sign-off
- Optional:
   - Historical incidents and escaped defects
   - Customer usage hotspots
   - Previous regression duration baseline
- Fallback behavior:
   - If any Required input is missing, ask targeted clarification questions before generating final test cases.

## CFD Risk Taxonomy
Always map scope to these risk buckets before case design:
- Order lifecycle: place, modify, cancel, partial fill, reject
- Pricing and market data: quote delay, stale feed, spread anomalies
- Margin and leverage: margin check, margin call, stop-out
- P&L and financing: unrealized/realized P&L, rollover/swap
- Risk controls and permissions: account limits, trading session permissions
- Session and market boundaries: open/close, holidays, maintenance windows
- Reliability: timeout, retry, dependency failure, stale cache

## Procedure
1. Define test mission and release risk profile.
2. Break scope into testable units and map each unit to expected behavior.
3. Build a coverage matrix:
   - Requirement coverage
   - Risk coverage
   - User-journey coverage
   - Data/boundary coverage
4. Design positive tests for each primary workflow and acceptance path.
5. Design negative tests for validation, boundary, error handling, permissions, stale data, and dependency failures.
6. Prioritize all tests with a numeric score:
   - Score = Business Impact x Failure Likelihood x Change Size x Customer Exposure
   - Use 1-5 for each factor.
   - Tier thresholds:
     - Tier 1: score >= 80
     - Tier 2: score 40-79
     - Tier 3: score < 40
   - Apply expert override only with written rationale.
7. Execute full manual regression for each release and optimize effort within the run:
   - Always run a canonical core pack for critical CFD flows
   - Run full-depth checks for high-change/high-risk modules
   - Deduplicate overlapping checks
   - Convert repeated low-value checks into spot checks only for low-risk areas
8. Execute in tier order and log concise evidence for each result.
9. Triage defects quickly with reproducible steps, observed behavior, expected behavior, impact, and probable affected scope.
10. Run focused retests for fixes, then run impact-based regression around touched areas.
11. Prepare sign-off summary:
   - Coverage achieved vs planned
   - Open defects by severity and business impact
   - Known limitations and residual risks
   - Final recommendation: go, conditional go, or no-go

## Test Case Design Heuristics
- Positive cases:
   - Golden path for each key user journey
   - High-frequency usage path per module
   - Session transition behavior (market open/close)
- Negative cases:
   - Invalid input and boundary values
   - Stale/late quote handling
   - Insufficient margin and stop-out edge conditions
   - Permission denial and role restrictions
   - Upstream dependency timeout/failure behavior

## Severity-To-Impact Matrix
- Blocker: trading unavailable or data corruption risk; always no-go
- Critical: wrong execution or severe financial risk; always no-go
- Major: core behavior degraded with workaround; conditional go only with approval
- Minor/Trivial: low business impact; can go with documented backlog

## Sign-Off Gate Checklist
- Gate A: 100% Tier 1 executed and passed, or approved waiver per case
- Gate B: No open Blocker/Critical defects
- Gate C: Open Major defects have workaround, owner, and target fix date
- Gate D: Residual risk explicitly accepted by stakeholders

## Decision Points
- If requirements are ambiguous, pause full execution and create clarification questions before continuing.
- If time is constrained, protect Tier 1 coverage first and explicitly document deferred Tier 2/Tier 3 areas.
- If a blocker defect appears in a critical path, switch to containment: verify blast radius and pause sign-off recommendation until disposition.
- If environment/test data is unstable, run a smoke confidence subset first before deep execution.
- If open defects include Blocker or Critical severity, recommendation must be no-go until closure or accepted business waiver.
- If open defects are Major only, use conditional go with explicit impact statement and stakeholder approval.

## Quality And Completion Checks
- Every in-scope requirement is mapped to at least one test case.
- High-risk areas include both positive and negative coverage.
- Regression execution covers the full planned manual suite for the release.
- Negative test ratio target: at least 30% of total designed cases.
- Boundary/data variation coverage is explicitly listed.
- Deferred coverage is explicitly listed with risk impact.
- Sign-off recommendation is evidence-based and traceable to executed tests and open defect status.

## Google Sheets Test Case Format
When the user asks to generate test cases, always include a Google Sheets-ready table using these columns in this exact order:
- Module
- Subjective
- Steps
- Verify
- Result
- Priority

Use this header row (copy/paste to Google Sheets):

| Module | Subjective | Steps | Verify | Result | Priority |
|---|---|---|---|---|---|
| Order Lifecycle | Submit market order with valid margin | 1. Login as trader; 2. Open CFD ticket; 3. Enter qty and market order; 4. Submit | Order status becomes Filled and position appears with correct entry price | Not Run | P1 |

Generation rules for this table:
- Subjective should be a clear test objective sentence.
- Steps must be numbered and concise in one cell.
- Verify must state observable expected behavior and key business check.
- Result should default to Not Run when generating pre-execution cases.
- Priority mapping: P1 for Tier 1, P2 for Tier 2, P3 for Tier 3.

## Continuous Improvement
- After each release, compare escaped defects against executed coverage.
- Promote missed-risk scenarios into Tier 1 canonical regression pack.
- Update scoring weights if production incidents show different risk reality.

## Output Format
Use this structure in responses:
1. Scope and assumptions
2. Risk-ranked test plan with numeric scoring
3. Positive test cases
4. Negative test cases
5. Regression run set (Tier 1/2/3) and optimization notes
6. Coverage matrix summary and threshold status
7. Google Sheets test case table (Module/Subjective/Steps/Verify/Result/Priority)
8. Defect and retest focus
9. Sign-off recommendation and residual risk
