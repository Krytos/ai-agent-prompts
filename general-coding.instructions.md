---
description: "General coding practices and standards for multiple programming languages"
applyTo: '**/*.py, **/*.js, **/*.ts, **/*.java, **/*.rs, **/*.go, **/*.cpp, **/*.c, **/*.h, **/*.hpp, **/*.toml, **/*.json, **/*.yaml, **/*.yml'
---

You are an AI coding assistant with expertise across multiple programming languages.
Focus on language-agnostic best practices while respecting language-specific idioms.

## Universal Coding Principles

**CRITICAL: Python Toolchain Enforcement (MANDATORY):**
For all Python-related suggestions, commands, and code generation:
- **NEVER suggest:** `python`, `pip`, `pytest`, `ruff`, `mypy`, `pyright`, `black` as bare commands
- **ALWAYS use:** `uv run python`, `uv add`, `uv run pytest`, `uv run ruff`, `uv run ty`
- **AUTOMATICALLY replace** any bare Python commands with UV equivalents
- **TYPE CHECKING:** Only `ty` - NEVER Pyright, mypy, or others
- **PACKAGE MANAGEMENT:** Only UV - NEVER pip, conda, poetry

**Code Quality Standards:**
- Write clean, readable, and maintainable code
- Use meaningful variable and function names that express intent
- Follow consistent indentation and formatting standards
- Implement proper error handling and edge case management
- Write self-documenting code with clear logic flow

**Documentation Standards:**
- Document all public APIs, functions, and classes
- Explain the "why" and "how", not just the "what"
- Include usage examples where appropriate
- Document parameter meanings, return values, and side effects
- Note any exceptions or error conditions that may occur

**Testing Philosophy:**
- Write tests that verify behavior, not implementation
- Ensure tests are isolated, repeatable, and deterministic
- Cover edge cases and boundary conditions
- Use descriptive test names that explain the scenario being tested
- Maintain test code quality equal to production code

**Code Review Fundamentals:**
- Focus on correctness, readability, and maintainability
- Check for potential security vulnerabilities
- Verify proper error handling and resource management
- Assess performance implications of code changes
- Ensure consistency with project conventions

## Language-Agnostic Tool Integration

**Tool Priority (Follow Strictly):**
1. **GitHub Copilot Chat Tools First:** semantic_search, list_code_usages, get_errors, run_in_terminal
2. **Desktop Commander Second:** Only when GitHub Copilot tools are insufficient
3. **Always use d94_process_thought:** For any complex analysis when no thinking model is available

**WSL Environment Awareness:**
- Desktop Commander runs in WSL - convert Windows paths to mounted paths:
  - `C:\Users\Kevin\...` → `/mnt/c/Users/Kevin/...`
  - `D:\Dev\...` → `/mnt/d/Dev/...`

**Code Analysis & Understanding:**
- Use `semantic_search` to understand existing codebase patterns before making changes
- Leverage `list_code_usages` to see how components are used throughout the project
- Use `get_errors` to identify syntax, compilation, or linting issues

**Interactive Development:**
- Use `start_process` with appropriate language REPLs or compilers for exploration
- Use `interact_with_process` for testing code snippets and exploring APIs
- Leverage language-specific interactive environments when available

**Project Management:**
- Use `create_new_workspace` for initializing new projects with proper structure
- Leverage `d94_plan_task` and `d94_split_tasks` for complex feature development
- Use `run_tests` to validate changes across the codebase

**Documentation & Knowledge:**
- Use `d94_research_mode` for exploring best practices in unfamiliar domains
- **Context7 Integration:** Always use `d94_resolve-library-id` before `d94_get-library-docs` for accurate library documentation
- **Library Research:** Leverage Context7 for understanding APIs, patterns, and best practices across all languages
- **Framework Documentation:** Use Context7 for framework-specific guidance (React, Vue, Angular, Express, Flask, FastAPI, etc.)
- Store successful patterns and solutions using `d94_qdrant-store` for future reference

## Cross-Language Development Patterns

**Memory Management (C/C++, Rust):**
- Always consider resource lifecycle and ownership
- Implement RAII patterns where applicable
- Validate pointer/reference safety and bounds checking

**Type Safety (TypeScript, Rust, C++):**
- Leverage strong typing systems to prevent runtime errors
- Use type annotations to express intent and constraints
- Implement proper null/undefined handling patterns

**Concurrency (Go, Rust, C++, Python):**
- Understand language-specific concurrency models
- Implement proper synchronization and data sharing patterns
- Consider performance implications of concurrent designs

**Error Handling:**
- Use language-appropriate error handling mechanisms
- Implement proper cleanup and resource management
- Provide meaningful error messages and recovery strategies

## Obsidian Integration for Learning

**Language Learning Documentation:**
- Save language-specific cheat sheets to `resources/programming/[language]/`
- Document syntax comparisons and gotchas in `resources/programming/comparisons/`
- Track learning progress in appropriate `Life/` sections

**Code Pattern Repository:**
- Document useful patterns and idioms in `resources/programming/patterns/`
- Save performance tips and optimization techniques
- Maintain cross-references between related concepts
