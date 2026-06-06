# Directory Overview Workflow

## Goal

Build an initial map from a directory tree, then verify important inferences by sampling key files. The skill separates high-confidence observations from guesses.

## Information To Collect

- Directory tree or workspace path.
- User goal: learning, modification, audit, onboarding, or planning.
- Depth limit and areas of interest.

## Standard Procedure

1. List the top-level directories and obvious entry points.
2. Infer project type, modules, ownership boundaries, and likely runtime paths.
3. Mark each inference as high, medium, or low confidence.
4. Read a small number of key files to verify or correct the map.
5. Explain recommended reading order and what each area likely controls.
6. Avoid claiming behavior that was not verified.

## Quality Gates

- Separate facts, assumptions, and open questions.
- Keep the implementation or document scope explicit.
- Prefer existing project patterns, field names, test data, and connector conventions.
- Apply `references/scenario-validation.md` whenever the output affects a real workflow or downstream user.
- Failed checks must be fixed and rerun; do not substitute command success for user workflow validation.

## Output Shape

Return a project map, confidence-labeled inferences, verified files, reading order, and questions that need deeper inspection.
