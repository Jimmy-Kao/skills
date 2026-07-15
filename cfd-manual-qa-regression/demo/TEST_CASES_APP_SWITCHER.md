# App Switcher Test Cases

## Scope and assumptions
- The exact requirement text and Figma node details were not readable in this environment.
- The cases below are a demo baseline for the app-switcher feature and should be refined once the readable requirement extract is available.

## Risk-ranked test plan with numeric scoring

| Risk | Impact | Likelihood | Change Size | Exposure | Score | Tier |
|---|---|---:|---:|---:|---:|---|
| Wrong app/context selected | 5 | 4 | 4 | 5 | 400 | P1 |
| App list fails to load | 4 | 3 | 3 | 4 | 144 | P1 |
| Default selection incorrect | 4 | 3 | 3 | 4 | 144 | P1 |
| Permission-denied app shown | 5 | 2 | 3 | 3 | 90 | P1 |
| Loading or empty state unclear | 3 | 3 | 2 | 4 | 72 | P2 |

## Positive test cases

| Module | Subjective | Steps | Verify | Result | Priority |
|---|---|---|---|---|---|
| App Switcher | Open switcher and view available apps | 1. Open the app switcher entry point; 2. Wait for the list to load | The switcher shows the available apps/contexts without layout breakage | Not Run | P1 |
| App Switcher | Switch to another app/context | 1. Open the app switcher; 2. Select a different available app/context | The application switches to the selected target and reflects the new context correctly | Not Run | P1 |
| App Switcher | Default selection is visible | 1. Open the switcher from a logged-in session | The current app/context is preselected or clearly indicated according to the requirement | Not Run | P1 |
| App Switcher | Close the switcher without changing context | 1. Open the switcher; 2. Close it without selecting another app | The current context remains unchanged and no unexpected navigation occurs | Not Run | P2 |

## Negative test cases

| Module | Subjective | Steps | Verify | Result | Priority |
|---|---|---|---|---|---|
| App Switcher | No unauthorized app is shown | 1. Open the switcher using a user without access to some apps | Only authorized apps/contexts are displayed | Not Run | P1 |
| App Switcher | Handle empty state | 1. Open the switcher for a user with no available apps/contexts | The UI shows a clear empty state and does not crash or mislead the user | Not Run | P2 |
| App Switcher | Handle loading failure | 1. Simulate a network or service failure while opening the switcher | An error or retry state is shown and the user remains in the current context | Not Run | P1 |
| App Switcher | Preserve state on failed switch | 1. Start from an app; 2. Force the target switch to fail | The original context stays active and no partial switch is left behind | Not Run | P1 |

## Coverage gaps
- Need the exact trigger location and UI labels from the Figma screen.
- Need the exact list source and default selection rule.
- Need permission and entitlement rules from the requirement document.
- Need the expected behavior after selection: full navigation, modal close, or context refresh.

## App profile delta
- Add the exact entry point and trigger behavior.
- Add the list population rule and default selection rule.
- Add the post-switch behavior and session preservation rule.
- Add the loading, empty, and error state copy once confirmed.

## Skill Delta for next iteration
- Newly learned behavior: app switcher is a high-risk navigation/context feature.
- Questions to ask next: what apps are available, how is the default chosen, and what happens on failure.
- Assumption: users can switch between multiple trading contexts or apps from one UI entry point.
- Wording to promote into the skill: always verify selection, authorization, loading state, and failure rollback for context-switch features.
