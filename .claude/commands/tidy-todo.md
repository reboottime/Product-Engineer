---
description: Move completed tasks from all todo.[topic].md files to todo.completed.md
---

Move all completed tasks (marked with `[x]`) from all `/for-human/tasks/todo.[topic].md` files to `/for-human/tasks/todo.completed.md`.

Steps:

1. Find all todo.*.md files in /for-human/tasks/ (excluding todo.md and todo.completed.md)
2. Read each todo.[topic].md file
3. Find completed tasks (lines with `- [x]`)
4. Append them to todo.completed.md under today's date, organized by priority
5. Remove completed tasks from their source todo.[topic].md files
6. Keep priority structure intact in both source and destination
7. If a todo.[topic].md becomes empty after cleanup, leave it (human will delete if needed)

Use today's date as the section header in todo.completed.md.
