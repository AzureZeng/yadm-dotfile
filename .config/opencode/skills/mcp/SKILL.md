---
name: mcp
description: Guide the agent on when to prefer MCP server tools over native tools for efficiency
---

## Purpose

MCP servers provide specialized tools, but calling them consumes tokens. This skill helps the agent decide when MCP tools are beneficial vs. when native tools are more efficient.

## Prerequisites

This skill only applies when one or more of these MCP servers are configured in the session:

- rider
- microsoft-learn
- context7

If no MCP servers are enabled, ignore this skill entirely.

## Rules

Depending on which MCP servers are available, apply the relevant rules below.

### rider

**When to use:**

- Refactoring (JetBrains Rider supported refactors)
- Text search/replace in files by text or regex
- Debugging
- Terminal commands
- Database queries via Rider's database tools

**When not to use:**

- Simple file reads/writes — use native tools (Read, Write, Edit) instead
- Operations that don't require Rider's specific capabilities — Rider MCP calls are expensive

### context7

- **When to use**: Looking up library/API documentation, code generation examples, setup or configuration steps. Context7 provides up-to-date docs from authoritative sources.
- **When not to use**: General knowledge questions, conceptual explanations, or well-known APIs already in training data — those waste tokens.

### microsoft-learn

- **When to use**: Researching Microsoft-specific technologies (C#, F#, ASP.NET Core, Microsoft.Extensions, NuGet, Entity Framework, .NET runtime). Tools available: `microsoft_docs_search`, `microsoft_docs_fetch`, `microsoft_code_sample_search`.
- **When not to use**: Broad architectural questions, non-Microsoft technologies, or topics well-covered in training data — use native research instead.
