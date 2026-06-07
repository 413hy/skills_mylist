# Clarify Before Building Demo Workflow

## Goal

Build complete demos only after the core business loop is clear. The skill prevents shallow demo fragments by clarifying ambiguity, confirming scope, then validating the finished demo through realistic user interactions.

## Information To Collect

- Demo goal, target user, core business object, platform, and constraints.
- Must-have workflows, nice-to-have features, sample data, and visual expectations.
- Run command, environment, test accounts, and acceptance criteria.

## Standard Procedure

1. Ask the single highest-impact clarification question when the business loop is unclear.
2. Mirror the confirmed requirement, included scope, excluded scope, and success criteria.
3. Build the smallest complete runnable demo that covers the confirmed loop.
4. Use existing project patterns when inside a codebase.
5. Run the demo and test each user-visible workflow through the normal UI or command entry point.
6. Fix failures and rerun the failed scenario before delivery.

## Quality Gates

- Separate facts, assumptions, and open questions.
- Keep the implementation or document scope explicit.
- For high-risk demos such as payment, authentication, destructive actions, production integrations, or sensitive data, label the risk and scope boundary before implementation.
- Prefer existing project patterns, field names, test data, and connector conventions.
- Apply `references/scenario-validation.md` whenever the output affects a real workflow or downstream user.
- Failed checks must be fixed and rerun; do not substitute command success for user workflow validation.

## Output Shape

Deliver runnable files or changes, run instructions, scenario-test evidence, test account/sample data, and known limitations.
