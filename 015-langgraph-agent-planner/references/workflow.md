# LangGraph Agent Planner Workflow

## Goal

Plan a LangGraph workflow by defining state, nodes, edges, loops, interrupts, persistence, recovery, and tests before implementation. The skill focuses on graph behavior, not only node functions.

## Information To Collect

- Workflow goal, state fields, actors, tools, and persistence needs.
- Branching rules, loop limits, interrupts, and recovery expectations.
- Representative full-path scenarios.

## Standard Procedure

1. Decide whether LangGraph is justified compared with a simple chain or workflow.
2. Define State schema, nodes, edges, conditional routing, terminal states, and loop guards.
3. Specify interrupts, persistence, resume behavior, and failure recovery.
4. Create full-path scenario tests before implementation.
5. If implementation is requested, build nodes and graph according to the plan.
6. Validate complete graph paths, including rejection, retry, and interruption paths.

## Quality Gates

- Separate facts, assumptions, and open questions.
- Keep the implementation or document scope explicit.
- Prefer existing project patterns, field names, test data, and connector conventions.
- Apply `references/scenario-validation.md` whenever the output affects a real workflow or downstream user.
- Failed checks must be fixed and rerun; do not substitute command success for user workflow validation.

## Output Shape

Provide graph design, state schema, node contracts, edge conditions, recovery plan, scenario tests, and implementation notes if applicable.
