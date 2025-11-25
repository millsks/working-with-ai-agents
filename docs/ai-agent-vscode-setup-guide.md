# VS Code Setup Guide for AI Agents (GitHub Copilot)

## Overview

This guide provides best practices for structuring your projects and configuring VS Code to maximize effectiveness when working with AI coding assistants like GitHub Copilot.

---

## Essential Files for AI Context

### 1. `.github/copilot-instructions.md`

Create project-specific instructions for GitHub Copilot:

```markdown
# Project Context for GitHub Copilot

## Project Overview
[Brief description of what this project does]

## Tech Stack
- Language: [e.g., Python 3.11, TypeScript 5.0]
- Framework: [e.g., React 18, FastAPI]
- Database: [e.g., PostgreSQL, MongoDB]
- Testing: [e.g., Jest, pytest]

## Coding Standards
- Use [specific style guide, e.g., PEP 8, Airbnb]
- Prefer [functional/OOP/specific patterns]
- Always include type hints/annotations
- Write docstrings for all functions

## Architecture Patterns
- Follow [MVC/MVVM/Clean Architecture/etc.]
- Use dependency injection
- Separate concerns: [specific patterns]

## Naming Conventions
- Files: [snake_case/kebab-case/PascalCase]
- Functions: [camelCase/snake_case]
- Classes: [PascalCase]
- Constants: [UPPER_SNAKE_CASE]

## Testing Requirements
- Minimum coverage: [e.g., 80%]
- Test file naming: [pattern]
- Mock external dependencies