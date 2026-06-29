# Global AGENTS.md

## About Skills

- When a task involves MCP server tools (microsoft-learn, context7, github), first load the `mcp` skill to determine when to use MCP tools vs. native tools.

## Engram Memory

- When searching (`mem_search`, `mem_context`) or saving (`mem_save`) memories, always use **English** for queries and content to ensure optimal FTS5 retrieval performance.

### FTS5 CJK (Chinese, Japanese, Korean) text limitation
| Scenario | Example | Result |
|---|---|---|
| English words in content/body | `Redis` | ✅ Found |
| English words in title | `Japanese` | ✅ Found |
| Full Chinese title string | `架构决策` | ✅ Found |
| Full Japanese title string | `日本語のテスト` | ✅ Found |
| Full Korean title string | `한국어 테스트` | ✅ Found |
| Korean partial match in title (Hangul) | `한국어`, `테스트` | ✅ Found |
| Chinese/Japanese partial match in title | `架构`, `日本語` | ❌ Not found |
| Chinese phrases in content/body | `Redis 连接字符串` | ❌ Not found |

**Workaround**: Always include English keywords in both `title` and `content`. For CJK concepts add English alias (e.g., `架构决策 (architecture decision)`). Search using full title string.
