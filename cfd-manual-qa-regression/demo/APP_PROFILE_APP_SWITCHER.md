# App Switcher App Profile

## Status
Provisional. The linked requirement and Figma sources were not readable from this environment, so this profile only captures what is currently known and what still needs confirmation.

## Confirmed Facts
- Feature name: app switcher
- Domain: trading app navigation / context switching
- Source documents: requirement page and UI design link provided by the user

## To Confirm
- Available apps or accounts in the switcher
- Entry point location and trigger behavior
- Switch result: full app navigation, modal close, account/context change, or both
- Default selection rules
- Permission or entitlement rules
- Loading and error states
- Empty state behavior
- Any recent-app or pinned-app logic
- Whether the switch preserves login session and unsaved state

## Risk Areas
- Wrong app selected
- Silent context mismatch
- Incorrect default app or account
- Failure to load app list
- Loss of current state during switch
- Permission-denied scenarios

## Glossary
- App switcher: a UI control used to move between apps, accounts, or contexts within the trading experience
