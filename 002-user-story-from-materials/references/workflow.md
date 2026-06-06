# User Story From Existing Materials Workflow

## Goal

Convert rough source material into a User Story that product, engineering, and QA can act on. The skill extracts intent, value, boundaries, acceptance criteria, examples, and open questions instead of merely rewriting the source text.

## Information To Collect

- Source material and target format.
- User role, business goal, known scope, exclusions, dependencies, and deadlines.
- Target reader: product, engineering, QA, external customer, or task system.

## Standard Procedure

1. Read all provided material and identify facts, assumptions, missing details, and contradictions.
2. Mirror the inferred requirement when ambiguity could change scope.
3. Write the story with role, goal, value, scope, non-goals, assumptions, dependencies, and risks.
4. Create acceptance criteria that cover happy path, error path, boundary cases, permissions, and data states.
5. Attach validation examples that a QA or developer can actually run.
6. List open questions separately instead of hiding them in acceptance criteria.

## Quality Gates

- Separate facts, assumptions, and open questions.
- Keep the implementation or document scope explicit.
- Prefer existing project patterns, field names, test data, and connector conventions.
- Apply `references/scenario-validation.md` whenever the output affects a real workflow or downstream user.
- Failed checks must be fixed and rerun; do not substitute command success for user workflow validation.

## Output Shape

Deliver a structured User Story, acceptance criteria, example tests, assumptions, exclusions, dependencies, and unresolved questions.
