# Original Prompt Summary

The user wants Codex to use quota freely and avoid rushing a task just because token or quota budget may be low. If quota runs out or final validation cannot finish, Codex should wait for the next refresh and continue with a new prompt or automation-backed resume instead of claiming the task is done.

The desired behavior is modeled after an existing automation that resumed work in `E:\垃圾\skills\skills` after Codex CLI quota prevented full final regression. That automation preserved:

- the latest user requirement;
- completed work and validation already passed;
- the exact blocker and retry timing;
- the remaining validation runner;
- final report, install sync, commit, and push duties;
- directories that must not be uploaded, such as third-party skills.

The skill should make that behavior reusable: create durable handoff state and thread heartbeat/automation when possible, and never mark work complete until realistic validation and delivery are actually complete.
