# Effective GitHub Copilot Prompt Files (.prompt.md)

Research findings on the specific "Prompt Files" feature in GitHub Copilot, which allows for reusable, template-driven instructions.

## What are Prompt Files?

Prompt files are Markdown files with the extension `.prompt.md` that define reusable prompts. They allow you to standardize complex queries and context for your team.

## Location & Structure

- **Location**: You must store these files in `.github/prompts/` within your repository.
- **Extension**: Must end in `.prompt.md`.
- **Invocation**: In Copilot Chat, type `/` to see available prompts defined in these files.

## File Format

A `.prompt.md` file consists of two parts:

1.  **YAML Frontmatter**: Metadata about the prompt.
2.  **Markdown Body**: The actual prompt content.

### Example Structure

```markdown
---
name: refactor-component
description: Refactors a React component to use functional patterns
model: gpt-4
---

You are a Senior React Engineer.
Refactor the selected component to use functional components and hooks.
Ensure:

1. No class components.
2. Typscript interfaces for Props.
```

## Templating & Parameters

You can make prompts dynamic using template variables.

### 1. User Input

Ask the user for input when the prompt is invoked.

- **Syntax**: `${input:variableName}` or `${input:variableName:placeholder}`
- **Example**: `Refactor this code to use the ${input:framework:React/Vue} framework.`

### 2. Built-in Variables

- `${selection}`: The currently selected code.
- `${file}`: The active file.
- `${workspaceFolder}`: The root of the workspace.

## Best Practices

1.  **Descriptive Names**: The `name` field is what users type (e.g., `/refactor`). Keep it short and memorable.
2.  **Clear Descriptions**: The `description` helps users select the right prompt from the slash menu.
3.  **Context**: Use the body to set the "Persona" (Role), "Goal", and "Constraints".
4.  **Version Control**: Commit these files to git so the entire team shares the same standard prompts.

## Vs. Custom Instructions

- **Custom Instructions** (`.github/copilot-instructions.md`) are _always_ active and apply to _every_ chat.
- **Prompt Files** (`.github/prompts/*.prompt.md`) are _on-demand_ templates invoked by the user.

Use Prompt Files for specific tasks (e.g., "Write Unit Test", "Publish Package") and Custom Instructions for global rules (e.g., "Always use TypeScript").
