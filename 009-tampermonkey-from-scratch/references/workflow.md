# Tampermonkey Script From Scratch Workflow

## Goal

Create a Tampermonkey userscript from real page behavior. The skill covers page analysis, match rules, permissions, selectors, injection timing, persistence, error handling, installation, and browser validation.

## Information To Collect

- Target URL patterns, manual workflow, desired automation, and allowed permissions.
- Page HTML or access to the page, selectors, dynamic loading behavior, and login requirements.
- Persistence requirements, safety constraints, and validation steps.

## Standard Procedure

1. Understand the manual workflow and what should trigger the script.
2. Inspect the real page or representative HTML before choosing selectors.
3. Define @match, permissions, storage needs, and injection timing.
4. Implement the script with defensive selectors, idempotency, and user-visible fallback behavior.
5. Install or simulate installation in Tampermonkey.
6. Validate on the target page with realistic operations and fix selector/timing failures.

## Quality Gates

- Separate facts, assumptions, and open questions.
- Keep the implementation or document scope explicit.
- Prefer existing project patterns, field names, test data, and connector conventions.
- Apply `references/scenario-validation.md` whenever the output affects a real workflow or downstream user.
- Failed checks must be fixed and rerun; do not substitute command success for user workflow validation.

## Output Shape

Provide the userscript, installation steps, scenario-test evidence, limitations, and selectors or assumptions that may need maintenance.
