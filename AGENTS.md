# Learning preferences

- Explain changes for a Python beginner.
- Introduce one new concept at a time.
- Use clear variable names and small examples.
- Explain why a change helps.
- Keep notebook explanations and code consistent.

# Reference materials

- Example learning documents are in `references/`, relative to this file.
- Read documents relevant to the current task before suggesting or making changes.
- Use `references/python-notes.md` for Python concepts and explanations.
- Use `references/sqlite-notes.md` for the book tracker and database concepts.
- Use `references/exercises.md` for optional practice, working through one exercise at a time.
- These are editable examples, not a record of completed lessons. Do not assume I have finished an exercise or mastered a topic.

# Two-agent notebook review

When reviewing or changing notebook code in this project, delegate review to two subagents:

1. **Python reviewer:** Check Python correctness, readability, variable names, connection cleanup, and whether explanations suit a beginner. Read `references/python-notes.md` and relevant exercises.
2. **SQLite reviewer:** Check SQL queries, parameters, table structure, saved data, and whether rerunning cells causes duplicates or unexpected changes. Read `references/sqlite-notes.md` and relevant exercises.

- Give both reviewers the user's request and the relevant notebook code. Ask them to work independently and return concrete findings with cell references and suggested fixes.
- Keep both reviews read-only. The main agent makes any authorized edits so reviewers do not overwrite each other's work.
- Wait for both reviewers, check their findings, and combine them into one response. Prioritize correctness, then explain the most useful learning improvement one concept at a time.
- Keep work within the user's request. A request for review alone does not authorize edits.
- Use this workflow for notebook code work; answer general questions and make documentation-only changes directly.
- If subagents are unavailable, state that briefly and perform both reviews in the main chat.
