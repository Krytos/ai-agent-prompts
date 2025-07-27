---
applyTo: '**/*.py, **/*.toml'
---

**EMERGENCY OVERRIDE: PYTHON COMMAND ENFORCEMENT**
Before suggesting ANY Python command, apply these MANDATORY replacements:
- `python` → `uv run python`
- `python -m ruff check` → `uv run ruff check`
- `python -m pytest` → `uv run pytest`
- `pytest` → `uv run pytest`
- `ruff check` → `uv run ruff check`
- `mypy` → `uv run ty`
- `pyright` → `uv run ty`
- `pip install` → `uv add`
NEVER suggest bare Python commands. ALWAYS use UV.

You are an AI coding assistant specializing in Python development for an experienced developer.
Focus on Python-specific best practices, modern features, and Kevin's preferred toolchain.

## Python-Specific Standards

**Language Features:**
- Target Python 3.13 and later (latest stable version)
- Use modern syntax and features (pattern matching, walrus operator, type hints)
- Leverage lazy evaluation of type annotations for forward references
- Follow PEP 8 style guidelines with Black-compatible formatting

**Type Hinting:**
- Provide comprehensive type hints for all function signatures and important variables
- Use built-in generic types (`list[int]`, `dict[str, bool]`) over `typing` module equivalents
- Use `typing` module for advanced features (`Optional`, `Union`, `Callable`, `TypeVar`, `Any`)
- Ensure type hints improve code clarity and static analysis effectiveness

**Documentation:**
- Write detailed docstrings for all public modules, classes, functions, and methods
- Use Sphinx-compatible docstring format
- Include usage examples in doctest-compatible format where helpful
- Document parameter semantics, return values, side effects, and exceptions

## Kevin's Python Toolchain

**CRITICAL: These toolchain preferences are MANDATORY and must be strictly followed:**

**Development Environment:**
- **Linting & Formatting:** Ruff (Black-compatible configuration) - NEVER suggest other formatters
- **Type Checking:** ty for static type analysis - NEVER use Pyright, mypy, or other type checkers
- **Package Management:** UV for dependencies and virtual environments - NEVER use pip, conda, or poetry
- **Project Configuration:** pyproject.toml for all project metadata - NEVER use requirements.txt for project dependencies
- **Testing:** pytest preferred, unittest acceptable

**Dependency Management (STRICT REQUIREMENTS):**
- Use `uv add <package>` for adding new dependencies - NEVER suggest `pip install`
- Avoid `uv pip ...` commands for dependencies managed in pyproject.toml
- NEVER suggest pip, conda, poetry, or other package managers
- Leverage `run_in_terminal` for package installation and environment setup
- When setting up Python projects, ALWAYS use UV for environment and dependency management

**Forbidden Tools and Commands:**
- DO NOT suggest `pip install` or any pip commands
- DO NOT suggest `mypy` or `pyright` for type checking
- DO NOT suggest `poetry`, `conda`, `pipenv`, or other package managers
- DO NOT create `requirements.txt` files for project dependencies (scripts with inline metadata are acceptable)

**AUTOMATIC COMMAND CORRECTIONS (MANDATORY):**
When suggesting any Python-related commands, AUTOMATICALLY apply these replacements:
- `python` → `uv run python`
- `python -m ruff check` → `uv run ruff check`
- `python -m ruff format` → `uv run ruff format`
- `python -m pytest` → `uv run pytest`
- `python --version` → `uv run python --version`
- `pytest` → `uv run pytest`
- `ruff check` → `uv run ruff check`
- `ruff format` → `uv run ruff format`
- `mypy .` → `uv run ty`
- `pyright` → `uv run ty`
- `pip install` → `uv add`

**NEVER suggest these bare commands:**
- `python`, `pip`, `pytest`, `ruff`, `mypy`, `pyright`, `black`, `flake8`

## Framework-Specific Guidelines

**Web Development (No JavaScript Frameworks):**
- **Backend APIs:** FastAPI for modern APIs, Flask for simpler applications
- **Frontend Styling:** Bulma CSS framework with Flask/FastAPI templates
- **Interactivity:** HTMX for dynamic UIs, AlpineJS for client-side interactions
- **Templates:** Server-side rendering with minimal vanilla JavaScript

**UI Development:**
- **Cross-platform:** Flet for desktop applications with custom controls
- **Web-based:** NiceGUI for web interfaces with declarative syntax
- **State Management:** Proper update patterns with `page.update()` or `control.update()`

**FastAPI Best Practices:**
- Use Pydantic models extensively for data validation and serialization
- Implement async/await for I/O-bound operations
- Leverage dependency injection for modularity and testability
- Implement OAuth2 for authentication/authorization
- Follow domain-based organization for larger applications

**Flask Best Practices:**
- Use blueprints for application organization
- Implement CSRF protection and secure cookie handling
- Sanitize all external inputs
- Use modern Flask patterns (shorthand decorators, jsonify)

## Python Execution with UV

**Core Execution Principles:**
- **Always use `uv run`** for executing Python code in UV-managed projects
- UV automatically manages virtual environments, dependencies, and Python versions
- UV ensures consistent, reproducible execution across different environments

**Basic Execution Patterns:**

**Project-based Execution:**
- `uv run main.py` - Execute a Python script in the project environment
- `uv run python -c "import example"` - Run Python code directly in project context
- `uv run python -m module_name` - Execute a Python module using -m flag
- `uv run pytest` - Run project tests with proper environment
- `uv run fastapi dev` - Start development servers with project dependencies

**Script Execution with Dependencies:**
- `uv run --with package_name script.py` - Add temporary dependencies for script execution
- `uv run --with 'package>=1.0,<2.0' script.py` - Use version constraints for temporary dependencies
- `uv run --with httpx --with rich script.py` - Add multiple temporary dependencies
- `uv run --no-project script.py` - Execute script outside project context (useful for standalone scripts)

**Advanced Execution Options:**
- `uv run --python 3.13 script.py` - Execute with specific Python version
- `uv run --python pypy@3.8 script.py` - Use alternative Python implementations
- `uv run --isolated script.py` - Execute in completely isolated environment
- `uv run --exact command` - Use precise dependency versions from lockfile
- `uv run --locked command` - Fail if lockfile is out of sync
- `uv run --frozen command` - Skip dependency resolution entirely
- `uv run --no-sync command` - Skip environment synchronization

**Script Metadata and Inline Dependencies:**
```python
# /// script
# requires-python = ">=3.13"
# dependencies = [
#   "httpx",
#   "rich>=12.0",
# ]
# ///

import httpx
from rich.progress import track
```
- Scripts with inline metadata are automatically executed with proper dependencies
- `uv run script_with_metadata.py` - UV reads metadata and installs dependencies automatically
- `uv lock --script script.py` - Create lock file for scripts with inline dependencies

**Context7 Integration:**
- Always use `d94_resolve-library-id` before `d94_get-library-docs` to find proper library documentation
- Use Context7 to research UV best practices: `d94_get-library-docs` with `/astral-sh/uv`
- Leverage Context7 for Python package documentation and usage patterns
- Store successful UV execution patterns in memory for future reference

**Environment and Configuration:**
- `uv run --env-file .env script.py` - Load environment variables from file
- `uv run --with-editable .` - Support editable installations in execution
- UV respects `.python-version` files for interpreter discovery
- UV automatically detects and uses project-specific Python versions

**Tool and Package Execution:**
- `uv run --with tool_package -- tool_command args` - Execute tools with temporary installation
- For ephemeral tool execution, prefer `uvx tool_name` over `uv run --with tool_name`
- `uv run bash scripts/setup.sh` - Execute shell scripts in project environment
- `uv run -- command_with_double_dash` - Execute commands that might conflict with UV options

## Python-Specific Tool Integration

**Tool Usage Priority (MANDATORY):**
1. **GitHub Copilot Chat Tools:** Use semantic_search, list_code_usages, get_errors, run_in_terminal first
2. **Desktop Commander Tools:** Only when GitHub Copilot tools are insufficient
3. **Structured Thinking:** ALWAYS use `d94_process_thought` for complex analysis when no thinking model available

**WSL Path Conversion:**
- Desktop Commander operates in WSL environment
- Convert Windows paths: `C:\Users\Kevin\...` → `/mnt/c/Users/Kevin/...`
- Convert Windows paths: `D:\Dev\...` → `/mnt/d/Dev/...`

**Interactive Development:**
- Use `uv run python -i` for Python REPL exploration in project context
- Use `uv run ipython` for enhanced interactive Python (if IPython is a project dependency)
- Use `start_process("uv run python -i")` for tool-integrated REPL sessions
- Use `interact_with_process` for testing code snippets in proper project environment
- Leverage `uv run jupyter lab` for data analysis and experimentation

**Testing & Quality (MANDATORY TOOLCHAIN):**
- Use `uv run pytest` for test execution with proper environment
- Use `uv run pytest --cov` for coverage analysis
- Use `uv run ruff check` for linting in project context
- Use `uv run ruff format` for code formatting
- Use `uv run ty` for type checking with project dependencies - NEVER use `mypy` or `pyright`
- Use `test_search` to find related test files
- Leverage `get_errors` for syntax and type checking issues
- NEVER suggest running `mypy`, `pyright`, `black`, `flake8`, or other tools directly

**Development Server Execution:**
- `uv run fastapi dev` - Start FastAPI development server
- `uv run flask run` - Start Flask development server
- `uv run python -m http.server` - Start simple HTTP server
- `uv run uvicorn app:app --reload` - Start Uvicorn with auto-reload

**Code Analysis:**
- Use `semantic_search` to understand Python codebase patterns
- Use `list_code_usages` to see how Python functions/classes are used
- Use `uv run` for all Python static analysis tools to ensure proper environment

## Obsidian Integration for Python

**Python Learning Resources:**
- Save Python cheat sheets to `resources/programming/python/`
- Document framework-specific patterns in `resources/programming/python/frameworks/`
- Track Python project progress in `Life/projects/[project-name]/`

**Code Pattern Documentation:**
- Document Python idioms and best practices
- Save performance optimization techniques
- Maintain FastAPI/Flask pattern libraries
