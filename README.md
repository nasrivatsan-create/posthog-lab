
# posthog-lab

A small test page I built to learn PostHog hands-on. It uses test data only (fake user IDs, no personal data).

**Live page:** https://nasrivatsan-create.github.io/posthog-lab/

## What it tests

- **Custom events:** `signup_started` and `signup_completed`
- **Identify:** "Complete signup" identifies a random fake test user (`test-user-NNNNN`)
- **Funnel:** `signup_started` to `signup_completed`
- **Feature flag:** `new-signup-button` changes the button text when it evaluates to on
- **Flag stability:** the page compares the flag value before and after identify and shows if it changed

## How to run a clean test

1. Open the page. Click **Start signup**, then **Complete signup**.
2. Click **New test visitor** before the next run. PostHog does not allow re-identifying an already identified user as a different ID, so this resets to a fresh anonymous visitor.
3. Check PostHog Activity (Live) for the events.

## What works

- Events arrive and the funnel shows drop-off between the two steps.
- Anonymous activity merges into the identified test user.
- The flag evaluates and the page reacts once flags have loaded.

## What is unresolved

- An experiment on this flag: the flag is on/off, and PostHog experiments need a multivariate flag with at least two variants. Not finished yet.
- I have not yet found a case where the flag value changes after identify. The page is set up to show it if it happens.
- Session replay has not been reviewed in depth.
