# Global AGENTS.md

## About Skills

- When a task involves MCP server tools (microsoft-learn, context7, github), first load the `mcp` skill to determine when to use MCP tools vs. native tools.

## Engram Memory System — Language Requirement

Engram persistent memory uses FTS5 for full-text search and vector retrieval. FTS5's tokenizer, stemming, and ranking algorithms are optimized for English — non-English content will produce poor search results or be completely unreachable.

**All memory content written to Engram must be stored in English**, regardless of the language used in the conversation with the user. Specific requirements:

| Field | Requirement |
|-------|-------------|
| `mem_save` / `mem_update` `content` | Must be in English |
| `mem_save` `title` | Must be in English |
| `topic_key` | Must be in English |
| `mem_search` query keywords | Must be in English |

If the user communicates in another language, translate key information to English before saving. This ensures memories are always retrievable via FTS5 search.
