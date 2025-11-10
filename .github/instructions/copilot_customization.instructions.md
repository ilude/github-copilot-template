---
description: "Guidelines for creating and maintaining GitHub Copilot instruction files and prompt files with current best practices"
applyTo: ".github/{instructions/*.instructions.md,prompts/*.prompt.md}"
---

# Copilot Customization Instructions

## Research Requirements

**ALWAYS research current documentation before modifying Copilot instruction or prompt files.**

GitHub Copilot and VS Code Copilot features evolve rapidly. What worked last month may be deprecated or replaced with better approaches.

---

## Research Process

### Before Creating or Modifying Files

1. **Search for Current Documentation**
   - Use web search to find the latest VS Code Copilot documentation
   - Check GitHub's official Copilot documentation
   - Review VS Code release notes for Copilot changes

2. **Verify Frontmatter Fields**
   - Check supported YAML frontmatter properties and syntax
   - Validate against current official examples
   - Test that fields work as expected

3. **Review New Features**
   - Look for recently added capabilities
   - Check for file format changes
   - Identify deprecated features to avoid

4. **Validate Examples**
   - Ensure any examples follow current best practices
   - Test examples in actual VS Code environment
   - Update outdated syntax or approaches

---

## Key Research Areas

### Frontmatter Documentation
Search for current information on:
- Supported YAML frontmatter fields in `.instructions.md` files
- Valid properties for `applyTo` patterns (glob patterns, file types)
- New metadata fields or configuration options
- Proper syntax and formatting requirements
- Case sensitivity and special characters

### Prompt File Format
Research current standards for:
- `.prompt.md` file structure and frontmatter
- Supported `mode` values (agent, chat, etc.)
- Description field requirements and best practices
- Any new prompt customization features
- Integration with Copilot chat modes

### File Organization
Look for guidance on:
- Recommended directory structure for instruction files
- Naming conventions for instruction and prompt files
- Best practices for organizing multiple instruction files
- Integration with workspace settings
- Precedence rules when multiple files apply

---

## Recommended Search Queries

When researching, use these search terms:

```
"VS Code GitHub Copilot instructions.md frontmatter documentation"
"GitHub Copilot workspace instructions file format 2025"
"VS Code Copilot prompt.md file syntax"
"GitHub Copilot applyTo patterns documentation"
"VS Code Copilot instruction file best practices latest"
"GitHub Copilot custom instructions reference"
"VS Code Copilot chat modes documentation"
```

---

## Implementation Guidelines

### Before Creating/Modifying Files

1. **Research current documentation** using web search
2. **Validate frontmatter syntax** against official examples
3. **Check for deprecated features** or syntax
4. **Review new capabilities** that might be relevant
5. **Test in actual environment** before committing

### Frontmatter Best Practices

#### Instruction Files (.instructions.md)
```yaml
---
description: "Brief, clear description of what this file instructs"
applyTo: "**/*.py"  # Glob pattern or comma-separated patterns
---
```

**Common applyTo patterns:**
- `"**/*.py"` - All Python files
- `"**/*.{ts,tsx}"` - TypeScript and TSX files
- `"**/Dockerfile*"` - All Dockerfile variants
- `"**/.devcontainer/**"` - All devcontainer files
- `"**/tests/**/*.py"` - Python files in tests directories

#### Prompt Files (.prompt.md)
```yaml
---
mode: "agent"  # or "chat"
model: "gpt-5-mini"  # Optional: specify model
description: "Brief description of what this prompt does"
---
```

**Mode options (verify current):**
- `agent` - For autonomous execution
- `chat` - For interactive conversation
- Others may be available - check documentation

### Content Guidelines

1. **Write clear, actionable instructions**
   - Use imperative mood ("Use X", not "You should use X")
   - Be specific about requirements
   - Include examples when helpful

2. **Avoid overly complex logic**
   - Keep instructions straightforward
   - Break complex requirements into multiple files
   - Use clear section headings

3. **Test instructions with actual use cases**
   - Verify Copilot follows the instructions
   - Check for conflicting guidance
   - Ensure instructions are neither too broad nor too narrow

4. **Keep frontmatter minimal**
   - Only use documented, supported fields
   - Avoid experimental or undocumented properties
   - Test that patterns actually match files

---

## Validation Steps

Before committing instruction or prompt files:

1. **Check YAML frontmatter syntax**
   - Proper indentation (2 spaces)
   - Quotes around string values with special characters
   - Valid YAML structure (use a YAML validator)

2. **Verify applyTo patterns match real files**
   ```bash
   # Test glob pattern matches
   ls **/*.py  # Should match intended files
   ```

3. **Test that instructions are clear and actionable**
   - Ask: "Can Copilot follow this unambiguously?"
   - Check for contradictions with other instruction files
   - Ensure specificity without over-constraining

4. **Ensure compliance with current Copilot documentation**
   - All frontmatter fields are documented
   - Syntax follows latest conventions
   - No deprecated features used

---

## Common Frontmatter Fields

Based on research, commonly supported fields include:

### For .instructions.md files:
- `description` - Brief description of the instruction file's purpose
- `applyTo` - Glob pattern(s) for when these instructions apply

### For .prompt.md files:
- `mode` - Execution mode (agent, chat, etc.)
- `model` - Optional model specification
- `description` - Brief description of the prompt's purpose

**IMPORTANT:** Always verify current supported fields through web research before use.

---

## Error Prevention

### Avoid These Common Issues

❌ **Don't:**
- Use unsupported frontmatter fields
- Write incorrect YAML syntax in frontmatter
- Create `applyTo` patterns that don't match actual files
- Write overly complex or unclear instructions
- Use outdated syntax or deprecated features
- Assume documentation from 6+ months ago is current

✅ **Do:**
- Research current documentation first
- Use only documented, supported fields
- Test glob patterns match intended files
- Write clear, actionable instructions
- Keep frontmatter simple and valid
- Update regularly as Copilot evolves

### When Errors Occur

1. **Research current documentation again**
   - Features may have changed
   - Syntax may have evolved
   - New approaches may be available

2. **Simplify frontmatter to only supported fields**
   - Remove experimental properties
   - Use minimal valid configuration
   - Test with bare minimum first

3. **Validate YAML syntax**
   - Use online YAML validator
   - Check indentation carefully
   - Ensure proper quoting

4. **Test with minimal examples first**
   - Start simple, add complexity gradually
   - Verify each addition works
   - Document what works and what doesn't

---

## Maintenance

### Regular Updates

Instruction files should be reviewed periodically:

- **Quarterly:** Review for relevance and accuracy
- **After Copilot updates:** Check for new features or breaking changes
- **When issues arise:** Debug and update problematic instructions
- **During code reviews:** Improve based on team feedback

### Update Checklist

- [ ] Research latest Copilot documentation
- [ ] Check for new features that could improve instructions
- [ ] Update examples to reflect current project patterns
- [ ] Remove deprecated syntax or approaches
- [ ] Verify applyTo patterns still match correctly
- [ ] Test instructions work as expected
- [ ] Update comments explaining customization points

### Documentation Tracking

Keep notes on:
- Current Copilot version and features used
- Custom patterns or approaches that work well
- Which instruction files are most effective
- Breaking changes in Copilot updates
- Team preferences and conventions

---

## Integration with Project Standards

### Consistency Requirements

- **Follow project's existing instruction file patterns**
- **Maintain consistent formatting and style**
- **Use project-specific terminology and examples**
- **Align with project's development workflow**
- **Respect team conventions and preferences**

### Quality Assurance

1. **Test instruction effectiveness**
   - Use in actual development tasks
   - Gather team feedback
   - Monitor Copilot's adherence

2. **Gather feedback**
   - Are instructions clear to team members?
   - Does Copilot follow them correctly?
   - Are there conflicting instructions?

3. **Refine based on usage**
   - Update based on what works
   - Remove what doesn't help
   - Adjust specificity as needed

4. **Ensure no conflicts**
   - Check for contradictions between files
   - Verify precedence is clear
   - Test with overlapping applyTo patterns

---

## Example: Creating a New Instruction File

### Process:

1. **Research current best practices**
   ```
   Search: "VS Code Copilot instructions.md format 2025"
   ```

2. **Create file with valid frontmatter**
   ```markdown
   ---
   description: "TypeScript coding standards and best practices"
   applyTo: "**/*.{ts,tsx}"
   ---

   # TypeScript Standards

   ## Type Safety
   - Use strict mode
   - Avoid `any` type
   ...
   ```

3. **Test the pattern matches files**
   ```bash
   # Verify pattern works
   ls **/*.{ts,tsx}
   ```

4. **Validate YAML frontmatter**
   - Check indentation
   - Verify quotes
   - Test in YAML validator

5. **Test with Copilot**
   - Open matching file
   - Ask Copilot to generate code
   - Verify it follows instructions

6. **Iterate and refine**
   - Adjust based on results
   - Clarify ambiguous instructions
   - Add examples if needed

---

## Resources

### Official Documentation
- VS Code Copilot Documentation: https://code.visualstudio.com/docs/copilot
- GitHub Copilot Documentation: https://docs.github.com/copilot
- VS Code Release Notes: https://code.visualstudio.com/updates

### Community Resources
- GitHub Copilot Community Forums
- Stack Overflow (tag: github-copilot)
- VS Code GitHub Issues

### Validation Tools
- YAML Validator: https://www.yamllint.com/
- Glob Pattern Tester: https://globster.xyz/

---

## Customization Notes

**CUSTOMIZE THIS FILE** for your team:

1. **Add team-specific research requirements**
2. **Document your standard frontmatter fields**
3. **List your commonly used applyTo patterns**
4. **Add team conventions for instruction organization**
5. **Include project-specific validation steps**
6. **Document your review and update schedule**

**Source:** Consolidated from onboard, attempt-one, agent-spike

**See also:**
- All other `.instructions.md` files for examples
- `.github/prompts/*.prompt.md` for prompt examples
