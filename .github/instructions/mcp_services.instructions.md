---
description: "Quick reference for MCP (Model Context Protocol) tools and services integration"
applyTo: "**"
---

# MCP Services Reference

## Overview

This is an **optional reference file** for projects using the Model Context Protocol (MCP). MCP enables AI tools to access external services, documentation, and memory stores.

**If your project doesn't use MCP, you can safely delete this file.**

---

## What is MCP?

MCP (Model Context Protocol) is a standard for connecting AI tools to external data sources and services:

- **Context7** - Library documentation and code examples
- **Memory servers** - Knowledge graphs and persistent memory
- **Sequential thinking** - Multi-step planning tools
- **Custom servers** - Project-specific integrations

---

## Common MCP Tools

### Context7 (Library Documentation)

**Purpose:** Fetch up-to-date library documentation and code examples

**Common operations:**
```
1. resolve-library-id: Convert library name to Context7-compatible ID
   - Input: Library name (e.g., "react", "next.js")
   - Output: Context7 ID (e.g., "/vercel/next.js")

2. get-library-docs: Fetch documentation for a library
   - Input: Context7-compatible library ID, optional topic, token limit
   - Output: Focused documentation snippets
```

**Resources:**
- Context7 GitHub: https://github.com/upstash/context7
- Installation guide: https://claudemcp.com/servers/context7

**Example workflow:**
```
1. Call resolve-library-id("next.js") → "/vercel/next.js"
2. Call get-library-docs("/vercel/next.js", topic="app router")
3. Use returned docs to inform code generation
```

---

### Memory MCP Servers (Knowledge Graphs)

**Purpose:** Store and retrieve structured knowledge across sessions

**Common operations:**
- `create_entities` - Create new nodes in knowledge graph
- `add_observations` - Add facts to existing entities
- `create_relations` - Link entities together
- `search_nodes` - Search by text or metadata
- `read_graph` - Export entire graph
- `delete_entities` - Remove nodes and relations
- `delete_observations` - Remove specific facts

**Use cases:**
- Project knowledge base
- Decision tracking
- Context persistence across sessions
- Relationship mapping

**Resources:**
- MCP servers gallery: https://code.visualstudio.com/mcp
- Model Context Protocol spec: https://modelcontextprotocol.io/

---

### Sequential Thinking MCP

**Purpose:** Multi-step planning and chain-of-thought reasoning

**Use cases:**
- Complex problem decomposition
- Multi-step workflows
- Planning with revision capability

**Note:** Implementations vary - check your specific server's documentation.

---

## Setting Up MCP in VS Code

### Installation

1. **Add MCP server to VS Code configuration**
   ```json
   // .vscode/mcp.json or settings.json
   {
     "mcp": {
       "servers": {
         "context7": {
           "command": "npx",
           "args": ["-y", "@upstash/context7-mcp"]
         }
       }
     }
   }
   ```

2. **Start the MCP server**
   - VS Code will automatically start configured servers
   - Or manually start via MCP inspector

3. **Verify connection**
   - Use MCP inspector to list available tools
   - Test basic operations

### Discovery

**Find available tools:**
```bash
# List all MCP tools in current session
# Use MCP inspector or listTools API
```

**Inspect tool signatures:**
- Check parameter names and types
- Review example payloads
- Understand return formats

---

## Integration Patterns

### Using Context7 for Documentation

```markdown
# When you need current library docs:

1. User asks about Next.js App Router
2. Resolve library: resolve-library-id("next.js")
3. Fetch docs: get-library-docs("/vercel/next.js", topic="app router")
4. Use returned docs to answer question accurately
5. Generate code using current best practices
```

### Using Memory for Project Context

```markdown
# Maintaining project knowledge:

1. At project start:
   - Create entities for key components
   - Document architecture decisions
   - Track dependencies and relationships

2. During development:
   - Add observations as features are built
   - Link related components
   - Update as changes occur

3. Between sessions:
   - Search nodes to recall context
   - Read graph for full project view
   - Continue where you left off
```

---

## MCP Tools Reference

### Function Naming Convention

MCP tools often have prefixed names:
- `mcp_context7_*` - Context7 library documentation
- `mcp_memory_*` - Memory/knowledge graph operations
- `mcp_sequential_*` - Sequential thinking tools

### Common Patterns

**Documentation lookup:**
```
mcp_context7_resolve-library-id("library-name")
mcp_context7_get-library-docs("context7-id", topic, tokens)
```

**Memory operations:**
```
mcp_memory_create_entities([{name, type, observations}])
mcp_memory_add_observations([{entityName, contents}])
mcp_memory_create_relations([{from, to, relationType}])
mcp_memory_search_nodes("query text")
```

---

## Best Practices

### When to Use MCP

✅ **DO use MCP when:**
- You need current documentation (library versions change)
- Maintaining context across multiple sessions
- Building knowledge graphs of project architecture
- Integrating external data sources

❌ **DON'T use MCP for:**
- Simple tasks that don't need external data
- Information available in local codebase
- One-off queries that don't need persistence

### Performance Considerations

- **Cache results** when appropriate
- **Batch operations** instead of multiple calls
- **Be specific** in queries to reduce data transfer
- **Clean up** unused entities to keep graphs manageable

### Error Handling

```markdown
If MCP call fails:
1. Check server is running
2. Verify authentication/API keys
3. Review parameter format
4. Check network connectivity
5. Fall back to alternative approach if needed
```

---

## Project-Specific MCP Configuration

### Custom MCP Servers

Document your project-specific MCP servers here:

```markdown
## Custom Server: ProjectDocs

**Purpose:** Access project-specific documentation

**Configuration:**
[Add configuration details]

**Available tools:**
[List tools and their usage]
```

### MCP Workflow Integration

Document how MCP fits into your workflow:

```markdown
## When to Query Context7

- Before implementing new library features
- When updating dependencies
- For current best practices

## When to Update Memory

- After architectural decisions
- When adding major features
- For deployment configurations
```

---

## Resources and Links

### Official Documentation
- Model Context Protocol: https://modelcontextprotocol.io/
- VS Code MCP integration: https://code.visualstudio.com/docs/copilot/chat/mcp-servers
- MCP servers gallery: https://code.visualstudio.com/mcp

### Specific Servers
- Context7: https://github.com/upstash/context7
- Context7 installation: https://claudemcp.com/servers/context7
- Claude MCP community: https://claudemcp.com/

### Tools
- MCP inspector (for testing)
- Server configuration examples
- Community-contributed servers

---

## Troubleshooting

### Common Issues

**Issue: MCP server not found**
```
1. Check .vscode/mcp.json configuration
2. Verify server installation
3. Restart VS Code
4. Check server logs
```

**Issue: Tool calls failing**
```
1. Verify server is running
2. Check parameter format
3. Review API authentication
4. Test with MCP inspector first
```

**Issue: Slow responses**
```
1. Reduce token limits in requests
2. Be more specific in queries
3. Check network connection
4. Consider caching results
```

---

## Customization Notes

**CUSTOMIZE THIS FILE** for your project:

1. **Remove if not using MCP** - This is optional
2. **Document your MCP servers** - Add project-specific integrations
3. **Add workflow examples** - Show how team uses MCP
4. **List available tools** - Document what's configured
5. **Include authentication** - Document API keys/credentials setup
6. **Add troubleshooting** - Project-specific issues and solutions

**DELETE THIS FILE** if your project doesn't use MCP services.

**Source:** Consolidated from onboard, attempt-one (MCP-enabled projects)

**See also:**
- `copilot_customization.instructions.md` for maintaining this file
- Project-specific MCP server documentation
