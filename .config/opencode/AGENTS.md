# Global AGENTS.md

## About Skills

- When a task involves MCP server tools (microsoft-learn, context7, rider, github), first load the `mcp` skill to determine when to use MCP tools vs. native tools.

## Memory (codemem)

### Session start — recall
At the start of every session (or when user references prior work), call:
```
codemem_memory_search_index(query="<brief task description>", limit=5)
```
If results are relevant, expand with `codemem_memory_get_observations` or `codemem_memory_timeline`.

### Task end — persist
After completing any non-trivial task (new feature, bugfix, refactor, decision), call:
```
codemem_memory_remember(
  kind="change|decision|discovery|bugfix|refactor|feature",
  title="<short title>",
  body="<what was done and why>",
  project="<project name>"
)
```

### Rules
- Always pass `project` when recording.
- Keep titles short and bodies high-signal.
- Use `codemem_memory_forget(id)` for incorrect or sensitive entries.
