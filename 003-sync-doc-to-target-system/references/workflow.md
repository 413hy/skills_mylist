# Sync Document To Target System Workflow

## Goal

Move or update a document, task, card, requirement, or story in a target system without losing meaning. The key requirement is post-sync verification of the target object, not just a successful API response.

## Information To Collect

- Source object, target system, target project or space, and field mapping.
- Authority rules for conflicting fields.
- Credentials or connector access, sync scope, and fields that must not be changed.

## Standard Procedure

1. Extract source fields, links, attachments, ownership, status, and acceptance criteria.
2. Map each source field to the target system and flag unsupported fields before writing.
3. Perform the sync or prepare exact sync instructions if credentials are missing.
4. Read back the target object after sync.
5. Compare source and target field by field, including links and attachments when available.
6. Report target links, mismatches, skipped fields, and required follow-up.

## Quality Gates

- Separate facts, assumptions, and open questions.
- Keep the implementation or document scope explicit.
- Prefer existing project patterns, field names, test data, and connector conventions.
- Apply `references/scenario-validation.md` whenever the output affects a real workflow or downstream user.
- Failed checks must be fixed and rerun; do not substitute command success for user workflow validation.

## Output Shape

Provide source-to-target mapping, target object link or id, verification table, mismatches, skipped fields, and next actions.
