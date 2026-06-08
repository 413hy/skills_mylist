# Operating Contract

## Hard Rules

- Understand the user goal before writing the final document. Do not silently expand a rough idea into a larger product scope.
- Prefer facts from local files, docs, tickets, existing requirements, or user-provided material before asking for missing information.
- Treat greenfield work as a valid project mode. Do not block only because no repo or code exists; state that the project is greenfield and capture stack/open-architecture questions.
- Ask focused clarification questions when a missing answer could change ownership, architecture, workflow, acceptance criteria, validation, or session split.
- Do not implement product code, create worker task files, or act as `session_0` unless the user explicitly changes the role.
- Separate facts, assumptions, open questions, contradictions, and decisions.
- The final development requirements document must stand alone. A downstream 012 window must not need the original chat to understand the need.
- If the user asks to proceed with incomplete information, make the gaps explicit and mark the handoff status as `Needs clarification`.

## Interaction Recipe

1. Identify whether the user wants clarification only, a final dev doc, or a doc prepared specifically for 012.
2. Read this skill's `SKILL.md`; load `references/workflow.md` for the full procedure.
3. Inspect relevant local material before asking questions when the user references a repo, file, report, ticket, or existing skill.
4. Maintain a compact requirement mirror instead of copying the conversation.
5. Use `references/dev-doc-template.md` when drafting the final document.
6. Use `references/scenario-validation.md` before delivery.

## Failure Handling

- If the target project path, source material, or expected reader is missing and cannot be inferred, ask for that one blocking detail.
- If source materials contradict each other, list the conflict and ask which source wins, unless the user asked for a draft with open questions.
- If the requirement is too broad for one document, create a top-level requirement document with clearly separated workstreams and note that 012 should decide the final session split.
- If validation shows the document cannot guide 012 or an implementer without hidden context, revise the document before delivery.

## Evidence Standard

For a finished document, validation evidence must include:

- The representative request or workflow used to test the document.
- Whether a downstream reader can identify goal, scope, non-goals, workflows, acceptance criteria, validation scenarios, risks, and open questions.
- Whether the document tells 012 to continue clarification or split sessions.
- Any missing information that blocks a confident handoff.
