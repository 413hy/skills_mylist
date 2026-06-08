# Original Prompt

This skill was created from a user request to add a requirements-focused skill that works before `012-codex-control-multisession`.

The desired flow:

1. The user talks with Codex in a new window to clarify the real requirement.
2. Codex writes a development requirements document from the clarified requirement.
3. The user sends that document to a window using `012-codex-control-multisession`.
4. 012 continues as `session_0`, reads the document as source material, and later handles multi-session routing.

The motivation is to avoid accumulating a large amount of exploratory requirements context inside the 012 control window.
