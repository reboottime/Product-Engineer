# Claude Code Technical Reference

Quick reference for Claude Code mechanics: context loading and tool configuration.

---

## Part 1: Context Loading

How agents, commands, and main conversation access CLAUDE.md.

### Memory Hierarchy (Main Conversation Only)

**Auto-loads at startup:**

1. Enterprise policy (`/Library/Application Support/ClaudeCode/CLAUDE.md`)
2. Project memory (`./CLAUDE.md` or `./.claude/CLAUDE.md`)
3. User memory (`~/.claude/CLAUDE.md`)
4. Project local (`./CLAUDE.local.md`)

**Recursive discovery:** Walks up from cwd to root, loads all CLAUDE.md files found.

### Context Access by Component

| Component | CLAUDE.md Access | How It Works |
|-----------|------------------|--------------|
| **Main conversation** | ✅ Auto-loaded | Loads all memory files at startup |
| **Custom agents** | ❌ Must explicitly read | Agent operates in isolated context; must use Read tool |
| **Slash commands** | ⚠️ Inherits from conversation | Only has context from the conversation that invoked it |

### Custom Agents

**Pattern:** Agents explicitly read CLAUDE.md

```markdown
# Agent workflow
1. Read `CLAUDE.md` → project context
2. Read relevant docs
3. Execute task
```

**Why:** Each agent runs in isolated context (prevents pollution). Must fetch context explicitly.

### Slash Commands

**Two ways to get CLAUDE.md context:**

1. **Inheritance:** Command inherits from main conversation (if CLAUDE.md already loaded)
2. **Explicit reference:** Use `@CLAUDE.md` in command invocation

**Default:** Commands only see context from invoking conversation, not auto-injected CLAUDE.md.

### Key Takeaway

**CLAUDE.md auto-loads for main conversation only.**

- Agents: Design them to explicitly read CLAUDE.md
- Commands: Rely on conversation inheritance or explicit @-mentions

---

## Part 2: Tool Configuration

Where and how to give your agents specific tools (Read, Grep, Bash, custom APIs, etc.)

### Three Contexts

| Context | Where | Use Case |
|---------|-------|----------|
| **Subagents** | `.claude/agents/` files | Custom agents in your project |
| **Agent SDK** | Code with SDK | Building standalone agents |
| **API Direct** | API calls | Full control, no CLI |

---

### Subagents (Most Common)

**When:** Creating custom agents like `product-manager`, `code-reviewer`

**Where:** `.claude/agents/your-agent.md`

#### Example

```markdown
---
name: code-reviewer
description: Reviews code for bugs and style issues
tools: Read, Grep, Glob
model: sonnet
---

You are a code reviewer. Check for:
- Logic errors
- Security issues
- Style consistency
```

#### Key Points

- **Optional field**: Omit `tools:` to give agent ALL tools
- **Available tools**: Read, Grep, Glob, Bash, Edit, Write, WebFetch, WebSearch
- **Quick setup**: Run `/agents` command for interactive tool picker

---

### Agent SDK (Custom Tools)

**When:** Building agents that need custom capabilities (database queries, API calls, file processing)

**Where:** Your agent code (TypeScript or Python)

#### TypeScript Example

```typescript
import { tool, createSdkMcpServer } from "@anthropic-ai/claude-agent-sdk";
import { z } from "zod";

// 1. Define your tool
const myTools = createSdkMcpServer({
  name: "database-tools",
  version: "1.0.0",
  tools: [
    tool(
      "query_users",                              // Tool name
      "Fetch users from database",                // Description
      { limit: z.number() },                      // Parameters (Zod schema)
      async (args) => {                           // Implementation
        const users = await db.query("SELECT * FROM users LIMIT ?", args.limit);
        return { content: [{ type: "text", text: JSON.stringify(users) }] };
      }
    )
  ]
});

// 2. Give it to your agent
const options = {
  mcpServers: { "database-tools": myTools },
  allowedTools: ["mcp__database-tools__query_users"]
};
```

#### Python Example

```python
from claude_agent_sdk import tool, create_sdk_mcp_server

# 1. Define your tool
@tool("query_users", "Fetch users from database", {"limit": int})
async def query_users(args):
    users = await db.query("SELECT * FROM users LIMIT ?", args["limit"])
    return {"content": [{"type": "text", "text": json.dumps(users)}]}

# 2. Create server
my_tools = create_sdk_mcp_server(
    name="database-tools",
    version="1.0.0",
    tools=[query_users]
)

# 3. Give it to agent
options = ClaudeAgentOptions(
    mcp_servers={"database-tools": my_tools},
    allowed_tools=["mcp__database-tools__query_users"]
)
```

#### Key Points

- Tools run in-process (fast, no separate server)
- Must use streaming input (async generator for prompts)
- Tool names become: `mcp__{server_name}__{tool_name}`
- Use `allowedTools` to restrict what agent can use

---

### API Direct (Advanced)

**When:** Calling Claude API without CLI or SDK

**Where:** Your API request code

#### Example

```python
import anthropic

client = anthropic.Anthropic()

response = client.messages.create(
    model="claude-sonnet-4-5-20250929",
    max_tokens=1024,
    tools=[
        {
            "name": "get_weather",
            "description": "Get current temperature for a location",
            "input_schema": {
                "type": "object",
                "properties": {
                    "location": {"type": "string", "description": "City name"}
                },
                "required": ["location"]
            }
        }
    ],
    messages=[{"role": "user", "content": "What's the weather in SF?"}]
)
```

---

## Quick Reference

**Starting out?** → Use subagents (`.claude/agents/`)

**Need custom tools?** → Use Agent SDK (in-process MCP servers)

**Building from scratch?** → Use API direct (full control)

---

## Resources

**Context Loading:**
- [Memory docs](https://code.claude.com/docs/en/memory.md)
- [Subagents docs](https://code.claude.com/docs/en/sub-agents.md)
- [Slash commands docs](https://code.claude.com/docs/en/slash-commands.md)

**Tool Configuration:**
- [Claude Code Subagents Docs](https://code.claude.com/docs/en/sub-agents.md#available-tools)
- [Agent SDK Custom Tools](https://platform.claude.com/docs/en/agent-sdk/custom-tools.md)
- [Claude API Tool Use](https://platform.claude.com/docs/en/agents-and-tools/tool-use/overview.md)
