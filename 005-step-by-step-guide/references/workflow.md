# Step-By-Step Guide Workflow

## Goal

Guide the user through a task one action at a time. This skill intentionally avoids dumping the full procedure when the next step depends on user feedback, logs, screenshots, or local observations.

## Information To Collect

- Final goal and current state.
- User environment, tools, permissions, and comfort level.
- What feedback the user can provide: output, screenshot, log, or observation.

## Standard Procedure

1. Confirm the immediate goal and any safety constraint in one short sentence if needed.
2. Give exactly one executable next step.
3. State exactly what output or observation the user should send back.
4. Wait for the feedback before choosing the next step.
5. When feedback arrives, decide whether it matches expectations and then provide the next single step.
6. Do not provide long background explanations unless the user asks.

## Quality Gates

- Separate facts, assumptions, and open questions.
- Keep the implementation or document scope explicit.
- Prefer existing project patterns, field names, test data, and connector conventions.
- Apply `references/scenario-validation.md` whenever the output affects a real workflow or downstream user.
- Failed checks must be fixed and rerun; do not substitute command success for user workflow validation.

## Output Shape

Each response should contain one step, the expected feedback, and at most a short reason when it helps execution.

Every response must start with an explicit step label such as `Step 1` or `第 1 步`, matching the user's language when obvious. Ask for exactly one feedback item. For browser login/debugging issues, prefer the simplest observable first, such as the visible error message; only move to DevTools/Network after that feedback if needed.
