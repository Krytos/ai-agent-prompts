---
description: "Essential global instructions - Kevin's toolchain preferences and environment handling"
applyTo: '**'
---

**PYTHON COMMAND ENFORCEMENT (MANDATORY)**
Auto-replace ALL Python commands:
- `python` → `uv run python` | `pip install` → `uv add` | `pytest` → `uv run pytest`
- `ruff check/format` → `uv run ruff check/format` | `mypy/pyright` → `uv run ty`
NEVER suggest bare Python commands.

**ENVIRONMENT PATH HANDLING (AUTO-APPLY)**
- **Desktop Commander tools:** WSL paths (`C:\` → `/mnt/c/`, remove URL encoding)
- **GitHub Copilot tools:** Windows paths (use as-is)

**PYTHON CODE QUALITY (AUTO-EXECUTE)**
After ANY Python edit: `uv run ruff format` → `uv run ruff check --fix` → `uv run ty check`

**MANDATORY SHRIMP PREPROCESSING (AUTO-EXECUTE)**
Before ANY complex action, MUST use appropriate SHRIMP tool:
- **Complex analysis/planning** → `d94_analyze_task` (REQUIRED first for systematic analysis)
- **Multi-step reasoning** → `d94_process_thought` (REQUIRED for structured thinking)
- **Research/exploration** → `d94_research_mode` (REQUIRED for systematic investigation)
- **Project breakdown** → `d94_plan_task` + `d94_split_tasks` (REQUIRED for task management)
- **Implementation guidance** → `d94_execute_task` (REQUIRED for guided execution)
- **Quality verification** → `d94_verify_task` (REQUIRED after completion)

**Auto-trigger Criteria (MANDATORY):**
- ANY request with 3+ coordinated steps
- Architecture or design decisions
- Multi-file operations or changes
- Learning new technologies or frameworks
- Debugging complex issues
- Project setup or configuration
- Problem-solving requiring systematic approach
NEVER bypass SHRIMP tools for complex operations.

## User & Memory
- User: Kevin
- Memory: Use `bb7_qdrant-find` at start, `bb7_qdrant-store` for new preferences
- **Knowledge Storage**:
  - **Global/General**: Use `bb7_qdrant-find` and `bb7_qdrant-store` for non-project knowledge
  - **Project-Specific**: Use project qdrant tool (check availability first)
- Categories: Identity, behaviors, preferences, goals, technical context, work patterns

## Tool Priority
1. **GitHub Copilot Tools** (Windows): `semantic_search`, `list_code_usages`, `get_errors`, `run_in_terminal`
2. **Desktop Commander Tools** (WSL): Desktop Commander tools (convert paths first)
3. **SHRIMP Task Manager**: Complex projects (`d94_plan_task`, `d94_split_tasks`)
4. **Context7**: Library documentation (`d94_resolve-library-id` → `d94_get-library-docs`)

## Kevin's Python Toolchain (MANDATORY)
- **Type Checking:** ONLY `ty` (never mypy/pyright)
- **Package Management:** ONLY UV (never pip/conda/poetry)
- **Config:** ONLY pyproject.toml (never requirements.txt)
- **Execution:** ALWAYS `uv run` for Python commands

## SHRIMP Methodology (Auto-trigger for complex tasks)
Apply for multi-file changes, new features, debugging, architecture decisions:
- **S**ystematic: `d94_analyze_task`, `d94_process_thought`
- **H**olistic: Query memory, consider complete context
- **R**esearch: `d94_research_mode`, Context7 documentation
- **I**terative: `d94_execute_task`, `d94_verify_task`
- **M**odular: `d94_plan_task`, `d94_split_tasks`
- **P**rocess: `d94_list_tasks`, systematic workflows

**Trigger Conditions:** Multi-file changes, new features, architecture decisions, debugging, learning new tech, project setup, 3+ coordinated steps

## Context7 Documentation
**Auto-use for:** Library docs, API references, framework patterns, version features, configuration
**Workflow:** `d94_resolve-library-id` → `d94_get-library-docs` → store with `bb7_qdrant-store`

## Information Lookup Priority (MANDATORY WORKFLOW)
**When seeking information, ALWAYS follow this order:**

1. **Check Qdrant Memory First:** Use `bb7_qdrant-find` to search for existing knowledge
   - Search for: Technical solutions, preferences, past decisions, learned patterns
   - If found and recent (< 3 months), use this information
   - If found but old (>= 3 months), proceed to Context7 for updates

2. **Check Obsidian Second:** Use `obsidian_simple_search` if qdrant has no results
   - Search for: Code patterns, learning notes, problem solutions, project decisions
   - Look in relevant directories: `resources/programming/`, `Life/projects/`
   - If found and recent, use this information

3. **Use Context7 for Current Info:** When information is missing, uncertain, or > 3 months old
   - Use for: Library documentation, API changes, framework updates, version-specific features
   - Always use latest/current information from Context7
   - Store new findings with `bb7_qdrant-store` for future reference

**Information Freshness Guidelines:**
- **< 1 month:** Use existing qdrant/Obsidian info confidently
- **1-3 months:** Use with caution, consider Context7 for critical decisions
- **> 3 months:** Always verify with Context7, especially for libraries/frameworks
- **Never found:** Start with Context7, then store in qdrant for future use

## Code Quality Standards
- Generate clean, maintainable code following language idioms
- Implement proper error handling and edge cases
- Write self-documenting code with clear intent
- Follow SOLID principles and security best practices

## Web Development Stack
- **Backend:** FastAPI (preferred) or Flask
- **Frontend:** HTMX + Bulma CSS + AlpineJS (NO React/Vue/Angular)
- **UI:** Flet or NiceGUI for desktop apps

## Obsidian Knowledge Management
**Auto-document insights when:** Learning concepts, solving problems, making decisions, discovering patterns

**Pattern Documentation:**
- **Universal Patterns:** `resources/programming/patterns/` - Cross-language design patterns
- **Language-Specific:** `resources/programming/[language]/patterns/` - Language idioms and best practices
- **Framework Patterns:** `resources/programming/[language]/frameworks/[framework]/patterns/` - Framework-specific implementations
- **Project Decisions:** `Life/projects/[project-name]/` - Architecture choices and trade-offs

**Knowledge Organization Workflow:**
1. **Search First:** Use `obsidian_simple_search` to find existing related notes
2. **Locate Directory:** Use `obsidian_complex_search` for similar concepts or decisions
3. **Check Structure:** Use `obsidian_list_files_in_dir` to understand organization patterns
4. **Place Strategically:** Choose most specific appropriate subdirectory
5. **Link Concepts:** Use `[[note-name]]` syntax to connect related ideas

**Content Categories:**
- **Learning Notes:** `resources/programming/[language]/features/` - New language features and syntax
- **Optimization:** `resources/programming/[language]/optimization/` - Performance techniques and best practices
- **Comparisons:** `resources/programming/comparisons/[concept]/` - Cross-language analysis
- **Problem Solutions:** `resources/programming/debugging/` - Debugging approaches and solutions
- **Tool Usage:** `resources/programming/tools/` - Development tool configurations and workflows

**Metadata & Linking:**
- Add relevant tags: `#python #patterns #api #optimization`
- Include frontmatter for better organization
- Document WHY decisions were made, not just WHAT was done
- Link to related concepts and create index pages for major topics

## Quick Commands
```bash
# Directory check
Get-Location

# Python workflow
uv run python script.py
uv run pytest
uv run ruff format && uv run ruff check --fix && uv run ty check

# Analysis
semantic_search "pattern"
list_code_usages function_name
get_errors
```
