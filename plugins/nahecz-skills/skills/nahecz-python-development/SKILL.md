---
name: nahecz-python-development
description: Python development instructions and best practices. Use when creating, modifying, refactoring, reviewing, or planning Python code and Python projects.
---

# Python development

This is used when writing (generating) code in Python.

## When to use this skill

- When working, modifying or generating Python code. Writing new code, refactoring old one. Always in this cases follow the rules defined in this skill.
- When planning new project and the implementation contains code written in python.

## General coding instructions

- Always produce strict typed code
- Prefer `pathlib.Path` for filesystem operations.
- Use builtin generics: list[...], dict[..., ...], etc. Do not use obsolete `List[...]`, etc. from typing module.
- Always annotated constants with `Final`. You don't need specify type with `[...]`.
- Every project should contain it's `pyproject.toml` file.
- Never specify module version in `__init__.py` file. Source of truth for the version is always `pyproject.toml`.
- Prefer `uv` as package manager instead of default `pip`. But do not change it in the project which already use `pip` only. Only for new projects.
- Prefer `ruff` as a main linter. But do not change it in the project if it uses another one, for example `flake8`.
- Never use relative imports, always full import naming.
- Prefer classes with static methods instead of modules with functions. main module is exception.
- Always make `TypeDict` for dicts with well-known structure
- Always use enums when multiple specifics are expected as a value. Use specific enums where it make sesnse (`StrEnum`, `IntEnum`, etc.).
- Use `match` instead `if ... elif` pattern where make sense. Especially when working with enums.
- Always make functions "private" with `_` prefix when these functions are not and should not be used outside the module.
- Always froze requirements with uv lock or pip tools on project which output is functional application. But do not froze requirements on projects which output is library.
- Define requirements in pyproject.toml. Do not use specific version here, only limit it with `>=`, `<`, etc. classificators.

## Testing specific instructions

- Use `pytest` as testing framework.
- Prefer `mockito` as mock testing library on new projects. Do not change when existing project use different one.

## Library specific instructions

### argparse

- Always use typed object namespace for argument parsing when multiple arguments are parsed.
