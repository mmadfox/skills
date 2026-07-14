# skills
My personal skills repository for LLM agents

## Table of Contents

- [Available Skills](#available-skills)
- [Loading Skills](#-important-loading-skills)

## Available Skills

### swag2mcp-format
Response formatting rules for swag2mcp MCP tools. Ensures consistent human-readable markdown, enforces pagination, colorizes HTTP methods, and structures schemas, headers, and errors for all swag2mcp tool responses.

📥 [Download](skills/swag2mcp-format/SKILL.md)

## 📌 Important: Loading Skills

> All models behave differently. While some models may automatically discover 
> and load skills, others require explicit instructions. To ensure consistent 
> and reliable behavior across different LLMs, we strongly recommend explicitly 
> loading skills at the start of each session.

### Recommended Workflow

Begin every session by loading the skills you need. This guarantees that the 
model has access to all instructions, templates, and resources regardless of 
its default behavior.

### Example Commands

Use these prompts to control skill loading:

| Action                      | Prompt                                                    |
|-----------------------------|-----------------------------------------------------------|
| List all available skills   | `Show all available skills`                               |
| Load all skills             | `Load all skills`                                         |
| Load a specific skill       | `Load the [skill-name] skill` (e.g., `Load the swag2mcp skill`) |

### Why This Matters

- Consistency – Ensures the same behavior across different models and sessions
- Control – You decide exactly which skills are active
- Transparency – Verify what's available before starting your task
- Reliability – Avoids assumptions about model auto-discovery capabilities
