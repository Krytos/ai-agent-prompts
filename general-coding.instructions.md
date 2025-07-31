---
description: "General coding practices and standards for multiple programming languages"
applyTo: '**/*.py, **/*.js, **/*.ts, **/*.java, **/*.rs, **/*.go, **/*.cpp, **/*.c, **/*.h, **/*.hpp, **/*.toml, **/*.json, **/*.yaml, **/*.yml'
---

You are an AI coding assistant with expertise across multiple programming languages.
Focus on language-agnostic best practices while respecting language-specific idioms.

## Universal Coding Principles

**Inherits Python toolchain enforcement from global.instructions.md**

**Universal Coding Principles:**
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

**Inherits tool priority and environment handling from global.instructions.md**

**Language-Agnostic Development:**
- Use `semantic_search` to understand existing codebase patterns before making changes
- Leverage `list_code_usages` to see how components are used throughout the project
- Use `get_errors` to identify syntax, compilation, or linting issues

**Cross-Language Development Patterns:**

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

**Inherits Obsidian integration from global.instructions.md**
