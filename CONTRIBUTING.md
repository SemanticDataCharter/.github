# Contributing to Semantic Data Charter Projects

Thank you for your interest in contributing to the **Semantic Data Charter (SDC4)** ecosystem! We welcome contributions from developers, researchers, documentation writers, and users around the world.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How Can I Contribute?](#how-can-i-contribute)
- [Getting Started](#getting-started)
- [Project-Specific Guidelines](#project-specific-guidelines)
- [Pull Request Process](#pull-request-process)
- [Coding Standards](#coding-standards)
- [Commit Message Guidelines](#commit-message-guidelines)
- [Community](#community)

## Code of Conduct

This project and everyone participating in it is governed by our [Code of Conduct](CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code. Please report unacceptable behavior to conduct@axius-sdc.com.

## How Can I Contribute?

### Reporting Bugs

Before creating bug reports, please check existing issues to avoid duplicates. When creating a bug report, include:

- **Clear title** describing the issue
- **Detailed description** of the problem
- **Steps to reproduce** the behavior
- **Expected vs actual behavior**
- **Environment details** (OS, Python/Node version, package version)
- **Code samples** or test cases if applicable

### Suggesting Enhancements

Enhancement suggestions are tracked as GitHub issues. When creating an enhancement suggestion:

- **Use a clear title** describing the enhancement
- **Provide detailed description** of the proposed functionality
- **Explain why this enhancement would be useful** to most users
- **List alternatives** you've considered
- **Include examples** of how the feature would work

### Contributing Code

1. **Fork the repository** you want to contribute to
2. **Create a feature branch** from `main`
3. **Make your changes** following project coding standards
4. **Add tests** for new functionality
5. **Ensure all tests pass**
6. **Update documentation** as needed
7. **Submit a pull request**

### Contributing Documentation

Documentation improvements are always welcome! This includes:

- README files
- API documentation
- User guides and tutorials
- Code examples
- Translations

### Translating Content

SDC4 is designed to be language-agnostic. We welcome translations of:

- Documentation
- User interfaces
- Examples
- Specification content

Supported languages include (but not limited to):
- Portuguese (pt-BR)
- French (fr-FR)
- Spanish (es-MX)
- Japanese (ja-JP)
- And more...

## Getting Started

### 1. Choose a Repository

The SDC4 ecosystem includes multiple repositories:

#### Core Repositories
- **[SDCRM](https://github.com/SemanticDataCharter/SDCRM)** - Reference model and specification
- **[sdc-xml2graph](https://github.com/SemanticDataCharter/sdc-xml2graph)** - XML to knowledge graph transformation
- **[SDCObsidianTemplate](https://github.com/SemanticDataCharter/SDCObsidianTemplate)** - Markdown templates

#### Validation Libraries
- **[sdcvalidator](https://github.com/Axius-SDC/sdcvalidator)** - Python validation library
- **[sdcvalidatorJS](https://github.com/Axius-SDC/sdcvalidatorJS)** - TypeScript/JavaScript implementation

### 2. Read Repository-Specific Guidelines

Each repository has its own:
- **CONTRIBUTING.md** - Contribution guidelines
- **CLAUDE.md** - Developer guide with architecture and coding standards
- **README.md** - Project overview and setup instructions

### 3. Set Up Your Development Environment

General requirements:
- **Git** for version control
- **GitHub account** for pull requests
- **Text editor or IDE** of your choice

Language-specific requirements are documented in each repository's CLAUDE.md.

## Project-Specific Guidelines

### Python Projects (sdcvalidator)

**Requirements:**
- Python 3.9+
- pytest for testing
- black, flake8, mypy for code quality

**Setup:**
```bash
git clone https://github.com/Axius-SDC/sdcvalidator.git
cd sdcvalidator
python -m venv venv
source venv/bin/activate
pip install -e ".[dev]"
pytest
```

**Standards:**
- PEP 8 compliance
- Type hints throughout
- 85% minimum test coverage
- Google-style docstrings

### TypeScript Projects (sdcvalidatorJS)

**Requirements:**
- Node.js 18+
- npm 9+
- Vitest for testing

**Setup:**
```bash
git clone https://github.com/Axius-SDC/sdcvalidatorJS.git
cd sdcvalidatorJS
npm install
npm test
```

**Standards:**
- TypeScript strict mode
- ESLint compliance
- 85% minimum test coverage
- TSDoc comments

### Django Projects (SDCStudio)

**Requirements:**
- Python 3.11+
- Docker and Docker Compose
- PostgreSQL, Redis (via Docker)

**Setup:**
```bash
git clone https://github.com/AxiusSDC/SDCStudio.git
cd SDCStudio
conda activate SDCStudio
docker-compose up -d
cd src
python manage.py migrate
python manage.py runserver
```

**Standards:**
- Django best practices
- Tailwind CSS for styling
- Comprehensive testing
- CUID2 for external IDs

### Schema/Specification Projects (SDCRM)

**Requirements:**
- XML/XSD knowledge
- RDF/OWL understanding
- Git for version control

**Standards:**
- XML Schema 1.1 compliance
- RFC process for schema changes
- Comprehensive documentation
- Working examples for all features

## Pull Request Process

### 1. Create a Feature Branch

```bash
git checkout -b feature/your-feature-name
# or
git checkout -b fix/bug-description
```

### 2. Make Your Changes

- Follow coding standards for the project
- Add tests for new functionality
- Update documentation
- Keep commits focused and atomic

### 3. Test Your Changes

```bash
# Python projects
pytest

# TypeScript projects
npm test

# Django projects
cd src && pytest
```

### 4. Commit Your Changes

Use conventional commit messages:

```bash
git commit -m "feat: add RDF generation for XdTemporal components"
git commit -m "fix: handle empty ExceptionalValue elements"
git commit -m "docs: update API documentation for validators"
```

**Commit types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation only
- `test`: Adding/updating tests
- `refactor`: Code refactoring
- `perf`: Performance improvement
- `chore`: Maintenance tasks
- `style`: Code style changes (formatting, etc.)

### 5. Push to Your Fork

```bash
git push origin feature/your-feature-name
```

### 6. Create Pull Request

- Provide clear title and description
- Reference related issues
- Complete the PR template checklist
- Request review from maintainers

### 7. Address Review Feedback

- Respond to comments promptly
- Make requested changes
- Push updates to your branch
- Request re-review when ready

### 8. Merge

Once approved, maintainers will merge your PR.

## Coding Standards

### General Principles

- **Readability** - Code is read more than it's written
- **Simplicity** - Prefer simple solutions over clever ones
- **Consistency** - Follow existing patterns in the codebase
- **Documentation** - Comment complex logic, document public APIs
- **Testing** - Write tests for new functionality

### Language-Specific Standards

#### Python (PEP 8)

```python
"""Module docstring explaining purpose."""

from typing import Optional, List
import os

class SDC4Validator:
    """Validator for SDC4 data packages.

    Args:
        schema_path: Path to SDC4 schema file
        strict: Enable strict validation mode

    Example:
        >>> validator = SDC4Validator('schema.xsd')
        >>> result = validator.validate('data.xml')
    """

    def validate(self, data_path: str) -> bool:
        """Validate SDC4 data against schema.

        Args:
            data_path: Path to data file

        Returns:
            True if valid, False otherwise

        Raises:
            FileNotFoundError: If data file doesn't exist
        """
        ...
```

#### TypeScript

```typescript
/**
 * Validator for SDC4 data packages.
 *
 * @example
 * ```typescript
 * const validator = new SDC4Validator('schema.xsd');
 * const result = await validator.validate('data.xml');
 * ```
 */
export class SDC4Validator {
  /**
   * Validate SDC4 data against schema.
   *
   * @param dataPath - Path to data file
   * @returns Validation result
   * @throws {FileNotFoundError} If data file doesn't exist
   */
  async validate(dataPath: string): Promise<boolean> {
    // ...
  }
}
```

### Testing Standards

- **Unit tests** for individual functions/classes
- **Integration tests** for component interactions
- **Coverage** minimum 85% for new code
- **Fixtures** for reusable test data
- **Descriptive names** for test functions

```python
def test_xdstring_validation_with_valid_value():
    """Test XdString validation accepts valid string value."""
    validator = SDC4Validator('test.xsd')
    result = validator.validate_component(
        '<XdString><value>test</value></XdString>'
    )
    assert result.is_valid
    assert len(result.errors) == 0
```

## Commit Message Guidelines

We follow **Conventional Commits** specification.

### Format

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Examples

```
feat(validator): add support for XdTemporal components

Implement XdTemporal validation including date, time, and datetime
formats. Add tests for all supported temporal formats.

Closes #123
```

```
fix(rdf): correct namespace URI generation

Namespace URIs were incorrectly including trailing slashes.
Fixed to match specification requirements.

Fixes #456
```

```
docs(readme): update installation instructions

Add conda installation method and troubleshooting section
for common setup issues.
```

### Subject Guidelines

- Use imperative mood ("add" not "added" or "adds")
- Don't capitalize first letter
- No period at the end
- Limit to 50 characters

### Body Guidelines

- Separate from subject with blank line
- Explain **what** and **why**, not **how**
- Wrap at 72 characters
- Can include multiple paragraphs

### Footer Guidelines

- Reference issues: `Closes #123`, `Fixes #456`, `Related to #789`
- Note breaking changes: `BREAKING CHANGE: description`

## Community

### Communication Channels

- **GitHub Issues** - Bug reports and feature requests
- **GitHub Discussions** - Questions and general discussion
- **Email** - contact@axius-sdc.com
- **LinkedIn** - [Axius SDC](https://www.linkedin.com/company/axius-sdc)

### Getting Help

1. **Check documentation** - README, CLAUDE.md, website
2. **Search issues** - Someone may have already asked
3. **GitHub Discussions** - Ask the community
4. **Email support** - For private concerns

### Recognition

Contributors are recognized in:
- CONTRIBUTORS file in each repository
- GitHub releases and changelogs
- Project documentation
- Annual contributor acknowledgments

### License

By contributing, you agree that your contributions will be licensed under the same license as the project:
- Most projects: **Apache 2.0**
- Check LICENSE file in specific repository

## Questions?

- **General questions**: Use GitHub Discussions
- **Security issues**: security@axius-sdc.com (see [SECURITY.md](SECURITY.md))
- **Code of Conduct concerns**: conduct@axius-sdc.com

---

**Thank you for contributing to SDC4!** Your efforts help build the foundation for trusted, interoperable data worldwide. 🌍

*Last Updated: November 2025*
