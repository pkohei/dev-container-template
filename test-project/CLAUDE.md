# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Python project called "test-claude-code" that uses modern development practices:
- **uv**: Modern Python package manager for fast dependency resolution and management
- **Docker**: Containerized development environment
- **Dev Containers**: VS Code integration for seamless container-based development

### Project Description

Testing Claude Code CLI integration

## Development Environment

This project uses DevContainer for consistent development environment across machines.

### Quick Start

1. Open the project in VS Code
2. Run "Dev Containers: Reopen in Container" from Command Palette
3. Install dependencies: `uv sync`
4. Start coding!

## Development Commands

### Package Management

```bash
# Install dependencies
uv sync

# Add new package
uv add package-name

# Add development package
uv add --dev package-name

# Update dependencies
uv lock --upgrade
```

### Running the Application

```bash
# Run the main module
uv run python -m test_claude_code.main
```

### Testing

```bash
# Run all tests
uv run pytest

# Run with coverage report
uv run pytest --cov

# Run specific test file
uv run pytest tests/test_main.py
```

### Code Quality

```bash
# Format code
uv run ruff format

# Run linting
uv run ruff check

# Auto-fix linting errors
uv run ruff check --fix
```

### Type Checking

```bash
# Run type checking
uv run mypy src
```

### Pre-commit Hooks

```bash
# Install pre-commit hooks
uv run pre-commit install

# Run hooks on all files
uv run pre-commit run --all-files
```

## Project Architecture

- **Source code**: `src/test_claude_code/` - Main application code
- **Tests**: `tests/` - Test files using pytest
- **Configuration**: `pyproject.toml` - Project configuration and dependencies
- **Dependencies**: `uv.lock` - Dependency lock file for reproducible builds
- **Docker**: `.devcontainer/` - Development container configuration
- **Production**: `Dockerfile.production` - Production-optimized Docker image

### Key Technologies

- **Python 3.12**: Programming language
- **uv**: Fast Python package manager
- **pytest**: Testing framework
- **ruff**: Code formatter and linter
- **mypy**: Static type checker
- **pre-commit**: Git hooks for code quality

## Development Guidelines

### Code Style
- Use `ruff format` for code formatting
- Follow ruff linting rules (`ruff check`)
- Add type hints to all functions and methods
- Run `mypy` before committing changes
- Follow Python naming conventions (PEP 8)
- Write docstrings for public functions and classes

### Testing
- Write tests for all new features
- Maintain test coverage above 80%
- Use descriptive test names
- Follow AAA pattern (Arrange, Act, Assert)

### Git Workflow
- Pre-commit hooks will run automatically before each commit
- Fix any issues reported by pre-commit hooks
- Write clear, descriptive commit messages
- Keep commits small and focused

## Production Deployment

### Building Production Image

```bash
# Build optimized production image
docker build -f Dockerfile.production -t test-claude-code:production .

# Run production container
docker run -p 8000:8000 test-claude-code:production
```

### Docker Optimization Features

- Multi-stage builds for smaller image size
- Official uv Docker images for efficiency
- Bytecode compilation for faster startup
- Security-focused (non-root user)
- Layer optimization for fast rebuilds

## Troubleshooting

### Common Issues

1. **Dependency conflicts**: Run `uv lock --upgrade` to resolve
2. **Import errors**: Ensure you're in the correct virtual environment
3. **Docker build issues**: Clear Docker cache with `docker system prune`

### Getting Help

- Check the project README.md for detailed setup instructions
- Review uv documentation: https://docs.astral.sh/uv/
- Dev Containers docs: https://containers.dev/