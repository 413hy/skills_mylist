# Pre-PR Check, Commit, and Pull Request Workflow

## Goal

Close out code changes before review. The skill is not just for running git commit; it verifies the changed behavior through realistic user workflows, keeps the commit scope clean, and prepares a reviewable pull request.

## Information To Collect

- Current branch, target branch, related issue or requirement.
- Changed behavior, user-visible workflows, and files that must stay out of scope.
- Test commands, dev server commands, test accounts, sample data, and required credentials.

## Standard Procedure

1. Inspect git status, recent commits, changed files, and relevant requirements before staging anything.
2. State the intended commit scope, excluded files, test plan, and unresolved assumptions.
3. Run existing static checks, unit tests, integration tests, build checks, or repository-specific verification.
4. Exercise every changed user-facing workflow with realistic data from the normal entry point.
5. Fix failures and rerun the failed scenario before committing.
6. Stage only the intended files, commit with a clear message, push the branch, and prepare or open the PR with verification evidence.

## Quality Gates

- Separate facts, assumptions, and open questions.
- Keep the implementation or document scope explicit.
- Prefer existing project patterns, field names, test data, and connector conventions.
- Apply `references/scenario-validation.md` whenever the output affects a real workflow or downstream user.
- Failed checks must be fixed and rerun; do not substitute command success for user workflow validation.

## Output Shape

Summarize changed scope, checks run, scenario tests, commit hash, branch, PR link or blocker, and residual risk.
