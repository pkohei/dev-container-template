# Dev Container Template

A comprehensive Copier template for creating Python development environments using:
- **uv**: Modern Python package manager for fast dependency resolution and management
- **Docker**: Containerized development environment
- **Dev Containers**: VS Code integration for seamless container-based development
- **Claude Code**: AI-powered code assistance integrated into the development environment
- **GitHub CLI**: Seamless repository and collaboration management
- **CUDA Support**: Optional GPU computing support for machine learning workloads

## Prerequisites

- Python 3.8 or higher
- Docker
- Visual Studio Code (recommended)
- Dev Containers extension (when using VS Code)

## Creating a Project from the Template

### 1. Install Copier

```bash
pip install copier
```

### 2. Generate the Project

```bash
# Generate from remote repository
copier copy https://github.com/your-username/dev-container-template my-awesome-project

# Generate from local template
copier copy . /path/to/new-project
```

### 3. Interactive Configuration

When running the template, you'll be prompted with the following questions:

- **Project name**: The name of the project
- **Project description**: A brief description of the project
- **Author name**: Your name
- **Author email address**: Your email address
- **Python version**: The Python version to use (choose from 3.11, 3.12, 3.13)
- **Enable CUDA (GPU) support**: Set to true for machine learning or GPU computing
- **CUDA version**: The CUDA version to use (choose from 11.8, 12.1, 12.2, 12.3, 12.4)
- **Ubuntu version**: Base Ubuntu version when using CUDA (choose from 20.04, 22.04)
- **Include pytest**: Set to true to use the testing framework (recommended)
- **Include Ruff**: Set to true to use code formatter and linter (recommended)
- **Include mypy**: Set to true to use type checker (recommended)
- **Include pre-commit**: Set to true to use Git hooks (recommended)
- **License**: The project license

## Using the Generated Project

### 1. Development with Dev Container

```bash
cd my-awesome-project
code .
```

After opening in VS Code, select "Dev Containers: Reopen in Container" from the Command Palette (Ctrl+Shift+P / Cmd+Shift+P).

### 2. Install Dependencies

```bash
uv sync
```

### 3. Development Commands

```bash
# AI-assisted development with Claude Code
claude-code

# Chat with Claude about your codebase
claude-code chat

# Run tests
uv run pytest

# Format code
uv run ruff format

# Run linting
uv run ruff check --fix

# Type checking
uv run mypy src
```

## Generated Project Structure

Projects created from this template will have:

```
my-awesome-project/
├── .devcontainer/          # DevContainer configuration
│   ├── devcontainer.json  # Dev Container settings
│   └── Dockerfile         # Development Dockerfile
├── src/
│   └── project_name/       # Main source code
├── tests/                  # Test files
├── pyproject.toml         # Project configuration and uv dependencies
├── uv.lock               # Dependency lock file
├── Dockerfile.production  # Production-optimized Dockerfile
├── .dockerignore          # Docker build context exclusions
└── README.md             # Project documentation
```

## Key Features

- **Fast Setup**: One command to create a fully configured Python project
- **AI-Assisted Development**: Claude Code CLI integration for intelligent code assistance
- **Modern Tooling**: Uses uv for dependency management, ruff for code quality
- **Container-Ready**: Includes Dev Container configuration for VS Code
- **GPU Support**: Optional CUDA/GPU support for machine learning and scientific computing
- **GitHub Integration**: GitHub CLI for seamless repository management
- **Flexible**: Optional components based on project needs
- **Type-Safe**: mypy configuration for type checking
- **Testing**: pytest setup with coverage reporting
- **Pre-commit**: Optional git hooks for code quality enforcement

## Customization

The generated project can be customized in the following ways:

### Adding New Dependencies

```bash
# Regular dependencies
uv add requests

# Development dependencies
uv add --dev black
```

### Editing Configuration Files

- `pyproject.toml`: Project configuration, dependencies, and tool settings
- `.devcontainer/devcontainer.json`: Dev Container configuration
- `.pre-commit-config.yaml`: Pre-commit hook configuration

## CUDA/GPU Support

When CUDA support is enabled:
- Uses NVIDIA CUDA development base image with selectable versions (11.8 - 12.4)
- Supports Ubuntu 20.04 and 22.04 base systems
- Includes GPU runtime configuration for Dev Containers (`--gpus=all`)
- Sets up CUDA environment variables automatically
- Requires NVIDIA Docker runtime on host system
- Suitable for PyTorch, TensorFlow, CuPy, and other GPU-accelerated libraries

## Troubleshooting

### Docker-related Issues

- Ensure Docker is running
- Verify that the Dev Containers extension is installed

### CUDA-related Issues

For CUDA-enabled projects:

- Verify that NVIDIA Docker is installed
  ```bash
  # Installation verification (adjust for your CUDA and Ubuntu versions)
  docker run --rm --gpus all nvidia/cuda:12.2-base-ubuntu22.04 nvidia-smi
  ```
- Ensure NVIDIA GPU drivers are installed on the host system
- CUDA containers take time to build initially (several GB download)

### uv-related Issues

```bash
# Install latest uv version
curl -LsSf https://astral.sh/uv/install.sh | sh

# Clear cache
uv cache clean
```

### Claude Code CLI Issues

```bash
# Check if Claude Code is available
claude-code --version

# Reinstall Claude Code CLI if needed
curl -fsSL https://download.anthropic.com/claude-code/install.sh | sh

# Get help with Claude Code commands
claude-code --help
```

### Template Updates

Apply template updates to existing projects:

```bash
copier update
```

## Docker Optimization

The template follows official uv Docker best practices:

- **Multi-stage builds**: Separate dependency and application layers
- **Official uv images**: `ghcr.io/astral-sh/uv:python{version}-bookworm-slim`
- **Bytecode compilation**: `UV_COMPILE_BYTECODE=1` for faster startup
- **Layer optimization**: Fast rebuilds when dependencies change infrequently
- **Production-ready**: Separate production Dockerfile with security optimizations

## Support

If you encounter issues, please refer to:

1. [Docker Official Documentation](https://docs.docker.com/)
2. [uv Official Documentation](https://docs.astral.sh/uv/)
3. [Dev Containers Official Documentation](https://containers.dev/)
4. [Copier Official Documentation](https://copier.readthedocs.io/)