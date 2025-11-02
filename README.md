# Semantic Data Charter Organization

This repository contains **organization-wide community health files** and governance documentation for the [Semantic Data Charter](https://semanticdatacharter.com) open source organization.

## Purpose

The `.github` repository provides default community health files that apply to all repositories in the SemanticDataCharter organization that don't have their own files.

**What's here:**
- **Organization profile** - Visible on https://github.com/SemanticDataCharter
- **Community health files** - CODE_OF_CONDUCT.md, CONTRIBUTING.md, SECURITY.md
- **Issue templates** - (future) Organization-wide issue templates
- **Workflow templates** - (future) Reusable GitHub Actions workflows

## Contents

### Profile

**`profile/README.md`**
- Organization profile displayed on the GitHub organization page
- Overview of SDC4 ecosystem
- Links to key repositories
- Quick start guides

### Community Health Files

**`CODE_OF_CONDUCT.md`**
- Contributor Covenant Code of Conduct v2.1
- Standards for community behavior
- Enforcement guidelines
- Reporting process

**`CONTRIBUTING.md`**
- How to contribute to SDC4 projects
- Development setup instructions
- Coding standards and guidelines
- Pull request process
- Commit message conventions

**`SECURITY.md`**
- Security policy for all SDC4 projects
- Vulnerability reporting process
- Security best practices
- Supported versions

## How It Works

GitHub automatically uses files from this repository as defaults when:
1. A repository in the organization **doesn't have** its own version
2. Someone opens an issue or PR in that repository
3. Someone views the organization profile

**Example**: If `SemanticDataCharter/some-repo` doesn't have a CODE_OF_CONDUCT.md, GitHub will use the one from this repository.

## Repository-Specific Files

Individual repositories can override these defaults by creating their own files. For example:

- **SDCRM** - Has repo-specific CONTRIBUTING.md with RFC process for schema changes
- **sdcvalidator** - Has Python-specific CONTRIBUTING.md and CLAUDE.md
- **sdcvalidatorJS** - Has TypeScript-specific CONTRIBUTING.md and CLAUDE.md

When a repository has its own files, they take precedence over these organization-wide defaults.

## SDC4 Ecosystem

This organization maintains the core specification and reference implementation for SDC4:

### Core Repositories
- **[SDCRM](https://github.com/SemanticDataCharter/SDCRM)** - Reference model, schemas, specification
- **[sdc-xml2graph](https://github.com/SemanticDataCharter/sdc-xml2graph)** - XML to knowledge graph transformation (Q1-2026)
- **[SDCObsidianTemplate](https://github.com/SemanticDataCharter/SDCObsidianTemplate)** - Markdown templates

### Related Organizations

- **[Axius-SDC](https://github.com/Axius-SDC)** - Commercial tools and validation libraries
  - sdcvalidator (Python)
  - sdcvalidatorJS (TypeScript)
- **[AxiusSDC](https://github.com/AxiusSDC)** - Commercial platform
  - SDCStudio (Django web application)

## Resources

- **Website**: https://semanticdatacharter.com
- **Specification**: [sdc4-specification.md](https://github.com/SemanticDataCharter/SDCRM/blob/main/sdc4/specification/sdc4-specification.md)
- **AI Instructions**: [ai.txt](https://semanticdatacharter.com/ai.txt)
- **Historical Archive**: [GitHub](https://github.com/Axius-SDC/historical-archive)

## Contributing to This Repository

Changes to organization-wide community health files should be:

1. **Well-justified** - Explain why the change benefits all projects
2. **Broadly applicable** - Work for diverse projects (Python, TypeScript, Django, schemas)
3. **Consensus-driven** - Discuss major changes with maintainers first
4. **Backward compatible** - Don't break existing repository-specific files

### Making Changes

```bash
git clone https://github.com/SemanticDataCharter/.github.git
cd .github

# Make changes
# Test by viewing in GitHub

git add -A
git commit -m "type: description"
git push origin main
```

## License

- **Community health files**: CC0 1.0 Universal (public domain)
- **SDC4 Specification**: Apache 2.0 (see individual repositories)

## Contact

- **General**: contact@axius-sdc.com
- **Security**: security@axius-sdc.com
- **Code of Conduct**: conduct@axius-sdc.com

---

**Building the future of trusted data together.** 🚀

*Last Updated: November 2025*
