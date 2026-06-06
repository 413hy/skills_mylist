# LangChain Agent Planner Workflow

## Goal

Plan a LangChain Agent before building it. The skill decides whether an agent is justified, defines tools, memory, schemas, guardrails, failure handling, and evaluation scenarios.

## Information To Collect

- Task goal, users, available tools, data sources, and constraints.
- Input/output schema, memory requirements, permissions, and failure behavior.
- Representative user queries and expected outcomes.

## Standard Procedure

1. Decide whether a LangChain Agent is necessary or a simpler workflow is enough.
2. Define tool list, tool contracts, retrieval sources, memory policy, and output schema.
3. Specify guardrails, escalation behavior, and observability requirements.
4. Create representative evaluation cases before implementation.
5. If implementation is requested, build the smallest agent that satisfies the plan.
6. Run scenario tests against realistic queries and failure cases.

## Quality Gates

- Separate facts, assumptions, and open questions.
- Keep the implementation or document scope explicit.
- Prefer existing project patterns, field names, test data, and connector conventions.
- Apply `references/scenario-validation.md` whenever the output affects a real workflow or downstream user.
- Failed checks must be fixed and rerun; do not substitute command success for user workflow validation.

## Output Shape

Provide architecture plan, tool contracts, memory policy, schemas, evaluation cases, scenario-test plan, and implementation notes if applicable.
