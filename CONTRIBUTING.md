# Contributing to Unified Knowledge Management System

Thank you for considering contributing to the Unified Knowledge Management System! This document provides guidelines and instructions for contributing to the project.

## Code of Conduct

By participating in this project, you agree to maintain a respectful and inclusive environment for everyone.

## How Can I Contribute?

### Reporting Bugs

- Check if the bug has already been reported in the [Issues](https://github.com/BjornMelin/unified-knowledge-system/issues)
- Use the bug report template when creating a new issue
- Include detailed steps to reproduce the bug
- Describe the expected behavior and actual behavior
- Include screenshots if applicable
- Specify your environment (OS, browser, versions)

### Suggesting Enhancements

- Check if the enhancement has already been suggested in the [Issues](https://github.com/BjornMelin/unified-knowledge-system/issues)
- Use the feature request template when creating a new issue
- Provide a clear description of the enhancement
- Explain why this enhancement would be useful
- Include examples of how the enhancement would work

### Pull Requests

1. Fork the repository and create a new branch from `develop`
2. Follow the [Git Workflow Standards](WORKFLOW.md)
3. Make your changes adhering to the coding standards
4. Add or update tests as needed
5. Update documentation to reflect changes
6. Submit a pull request to the `develop` branch
7. Ensure all CI checks pass

## Development Setup

1. Clone the repository
```bash
git clone https://github.com/BjornMelin/unified-knowledge-system.git
cd unified-knowledge-system
```

2. Set up the development environment
```bash
# Install dependencies for each component
cd mcp-servers/devdocs && npm install
cd ../firecrawl && npm install
cd ../qdrant && npm install
cd ../knowledge-graph && npm install
cd ../../integration/unified-search && npm install
cd ../supergateway && npm install
```

3. Configure local settings
```bash
# Copy example configuration files
cp config.example.js config.local.js
# Edit the configuration files as needed
```

## Coding Standards

### JavaScript/TypeScript
- Use ESLint and Prettier with the project's configuration
- Follow the Airbnb JavaScript Style Guide
- Use TypeScript where possible
- Write descriptive variable and function names
- Include JSDoc comments for all functions and classes

### Python
- Follow PEP 8 style guide
- Use type hints where possible
- Include docstrings for all functions and classes
- Use descriptive variable and function names

### Documentation
- Update documentation for any changed functionality
- Document all new features, APIs, and configuration options
- Follow the project's documentation style

## Testing

- Write unit tests for all new functionality
- Ensure all existing tests pass
- Aim for high test coverage
- Include integration tests for new features
- Test across multiple environments if relevant

## Commit Messages

Follow the [Conventional Commits](https://www.conventionalcommits.org/) specification:

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

Examples:
- `feat(search): add vector similarity search`
- `fix(qdrant): resolve connection timeout issue`
- `docs: update API documentation`

See [WORKFLOW.md](WORKFLOW.md) for more details on commit message standards.

## Review Process

1. All pull requests require at least one review before merging
2. Address all feedback in the review
3. Ensure all CI checks pass
4. Maintainers will merge approved pull requests

## Documentation

- Update documentation for any changed functionality
- Create or update API documentation
- Update any relevant examples
- Ensure documentation builds correctly

Thank you for contributing to the Unified Knowledge Management System!
