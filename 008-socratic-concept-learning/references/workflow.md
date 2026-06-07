# Socratic Concept Learning Workflow

## Goal

Help the user build understanding instead of passively receiving a lecture. The skill uses small questions, hints, examples, misconception checks, and a final concise summary.

## Information To Collect

- Concept, user level, goal, and preferred language or analogy style.
- Whether the user wants slow guidance, exam prep, or practical engineering understanding.
- Any prior explanation or confusion point.

## Standard Procedure

1. Name the target concept or concept set first, then start with a compact mental map.
2. Ask one diagnostic question at a time.
3. Use the user answer to choose the next hint, example, or correction.
4. Avoid long lectures unless the user asks for a full explanation.
5. Use one concrete scenario to test whether the concept transferred.
6. End with a short summary, common traps, and a memory hook.

## Quality Gates

- Separate facts, assumptions, and open questions.
- Keep the implementation or document scope explicit.
- In early turns, keep the response compact enough for the user to answer immediately. In the first reply, avoid fenced code blocks; use inline code or one single-line example unless the user explicitly asks for code.
- When correcting a misconception, explicitly say the idea is incomplete or not equivalent before guiding the user to test it.
- Prefer existing project patterns, field names, test data, and connector conventions.
- Apply `references/scenario-validation.md` whenever the output affects a real workflow or downstream user.
- Failed checks must be fixed and rerun; do not substitute command success for user workflow validation.

## Output Shape

Provide one question or correction per turn, then a final concise concept map, examples, misconceptions, and self-check question.

For the first turn, explicitly mention the target concept names before asking the first question. This keeps the Socratic prompt anchored even when the answer is intentionally short.
