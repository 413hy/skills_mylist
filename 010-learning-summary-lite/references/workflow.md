# Concise Learning Summary Workflow

## Goal

Summarize learning material into a compact version that is easier to understand and retain. The skill prioritizes structure, plain language, key terms, examples, misconceptions, and a quick self-check.

## Information To Collect

- Source material, target learner level, desired length, and focus.
- Must-keep sections, parts to skip, and preferred style.
- Whether examples, analogies, questions, or exam notes are needed.

## Standard Procedure

1. Identify the source scope and the learner level.
2. Extract the core structure before shortening details.
3. Explain key terms in plain language.
4. Keep essential examples and remove decorative or repeated material.
5. Add misconceptions or traps when the topic commonly causes confusion.
6. Use a small self-check scenario or question to verify understanding.

## Quality Gates

- Separate facts, assumptions, and open questions.
- Keep the implementation or document scope explicit.
- Prefer existing project patterns, field names, test data, and connector conventions.
- Apply `references/scenario-validation.md` whenever the output affects a real workflow or downstream user.
- Failed checks must be fixed and rerun; do not substitute command success for user workflow validation.

## Output Shape

Return a concise summary, key terms, minimal example, common mistakes, and one or more self-check questions.
