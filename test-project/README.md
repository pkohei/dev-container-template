# test-claude-code

Testing Claude Code CLI integration

## Development Environment Setup

This project provides a development environment using DevContainer.

### Prerequisites

- Docker
- Visual Studio Code
- Dev Containers extension

### Starting the Development Environment

1. Open the project in VS Code
2. Open the Command Palette (Ctrl+Shift+P / Cmd+Shift+P)
3. Run "Dev Containers: Reopen in Container"

### Dependency Management

This project uses [uv](https://docs.astral.sh/uv/) to manage Python dependencies.

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

### Docker Optimization

This project's Docker setup is optimized following official uv recommendations:

- **Multi-stage builds**: Separate dependencies and project code for improved cache efficiency
- **Official uv image**: Uses `ghcr.io/astral-sh/uv:python3.12-bookworm-slim`
- **Bytecode compilation**: `UV_COMPILE_BYTECODE=1` for faster startup
- **Cache mounts**: `--mount=type=cache` for faster build times
- **Layer optimization**: Fast rebuilds when dependencies change infrequently

### Running the Application

```bash
# Run the main module
uv run python -m test_claude_code.main
```

### Running Tests

```bash
# Run all tests
uv run pytest

# Run with coverage report
uv run pytest --cov

# Run specific test file
uv run pytest tests/test_main.py
```

### Code Formatting and Linting

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

### Production Deployment

An optimized Dockerfile for production is also provided:

```bash
# Build production image
docker build -f Dockerfile.production -t test-claude-code:production .

# Run in production environment
docker run -p 8000:8000 test-claude-code:production
```

## Project Structure

```
test-claude-code/
├── .devcontainer/          # DevContainer configuration
│   ├── devcontainer.json  # Dev Container settings
│   └── Dockerfile         # Development Dockerfile
├── src/
│   └── test_claude_code/   # Main source code
├── tests/                  # Test files
├── pyproject.toml         # Project configuration and uv dependencies
├── uv.lock               # Dependency lock file
├── Dockerfile.production  # Production-optimized Dockerfile
├── .dockerignore          # Docker build context exclusions
└── README.md             # This file
```

## License
This project is licensed under the MIT License.