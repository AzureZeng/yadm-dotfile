# Global AGENTS.md

## About Skills

- When a task involves MCP server tools (microsoft-learn, context7, github), first load the `mcp` skill to determine when to use MCP tools vs. native tools.

## Engram Memory

-*Always use English*: When calling `mem_save`, `mem_update`, `mem_search`, `mem_judge`, `mem_compare` etc., all FTS5-indexed fields (`title`, `content`, `query`, `reason`) MUST be in English. If the user writes in Chinese, translate before saving. Do not follow the user's language. Violation is a critical error.

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
