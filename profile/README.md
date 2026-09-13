# Semantic Data Charter

### The Deterministic Data Substrate for Autonomous Systems

The **Semantic Data Charter (SDC)** is an open specification for creating self-describing, semantically rich data models that work seamlessly across systems, languages, and autonomous agents.

> **This organization and all repositories within it are controlled and maintained by [Axius SDC, Inc.](https://axius-sdc.com)**

## Vision

**Data infrastructure engineered for fully automated machine processing.**

We saw where technology was heading 25 years ago: machines would become the primary consumers and producers of structured data. When that happened, every system built for human interpretation would break. SDC was built for that world.

- **Open** - Built on international standards, not proprietary lock-in
- **Accessible** - Language-agnostic, enabling global collaboration
- **Governed** - Built-in lineage and provenance for accountability
- **Permanent** - CUID-based immutability for long-term data integrity

## Core Principles

### Three Pillars of SDC

1. **Enforce Governance** - Built-in lineage and provenance tracking
2. **Embed Meaning** - Semantic interoperability via RDF/OWL
3. **Mandate Quality** - Validation rules and quality constraints

## What is SDC?

Think of it as: **"Protocol Buffers with semantics and governance"**

SDC combines:
- **Structure** (like Protocol Buffers) - XML Schema 1.1 for data types and constraints
- **Semantics** (like RDF/OWL) - Meaning and relationships
- **Validation** (like SHACL) - Quality rules and business logic
- **Governance** - Lineage, provenance, and audit trails
- **Packaging** - Self-contained, queryable data packages

**Result**: Data that is self-describing, semantically rich, and audit-ready - readable by machines without human interpretation.

## Key Features

- **Language Agnostic** - Model in Portuguese, French, Japanese, Spanish, etc.
- **Standards-Aligned** - Aligned with the vocabularies of 24 international standards from W3C, OASIS, OMG, ISO, IETF, and IANA
- **AI Governance** - Governance decision engine returning OASIS XACML decisions with tamper-evident receipts
- **Namespace Versioning** - CUIDs for immutable, evolvable components
- **Multi-Format Export** - RDF, OWL, SHACL, FHIR, GraphQL, JSON, GQL

## Use Cases

- **Enterprise Data Integration** - Canonical models for multi-system environments
- **AI Governance** - Data packages with automatic lineage for trustworthy AI
- **Cross-Border Exchange** - Semantic interoperability without translation
- **Regulatory Compliance** - Built-in audit trails and provenance
- **Legacy Modernization** - Bridge between old and new systems
- **Agentic Infrastructure** - Deterministic data substrate for autonomous agents

## SDC Ecosystem

### Core Repositories

- **[SDCRM](https://github.com/SemanticDataCharter/SDCRM)** v4.1.0 - Reference model, schemas, and specification ([releases](https://github.com/SemanticDataCharter/SDCRM/releases))
- **[sdc-xml2graph](https://github.com/SemanticDataCharter/sdc-xml2graph)** v4.0.0 - Transform SDC4 XML to knowledge graphs (Q1-2026)

### Template Creation

- **[Form2SDCTemplate](https://github.com/SemanticDataCharter/Form2SDCTemplate)** v4.4.0 - Convert PDF, DOCX, and image forms into SDC templates using Gemini AI. Available as a [Python package](https://pypi.org/project/form2sdc/), [Google Colab notebook](https://colab.research.google.com/github/SemanticDataCharter/Form2SDCTemplate/blob/main/notebooks/form_to_template.ipynb), or LLM instruction file.
- **[SDCObsidianTemplate](https://github.com/SemanticDataCharter/SDCObsidianTemplate)** v4.3.0 - Interactive Obsidian Templater plugin for building SDC markdown templates with guided prompts, domain-aware defaults, and SDC participation model support.

### Validation & Governance

- **[sdcvalidator (Python)](https://github.com/SemanticDataCharter/sdcvalidator)** v4.5.0 - SDC4 structural validator with two-tier error classification ([PyPI](https://pypi.org/project/sdcvalidator/))
- **[sdcgovernance (Python)](https://github.com/SemanticDataCharter/sdcgovernance)** v4.2.0 - Governance decision engine, aligned with the vocabularies of 24 standards from W3C, OASIS, OMG, ISO, IETF, IANA. Returns OASIS XACML decisions (PERMIT/DENY/INDETERMINATE/NOT_APPLICABLE) with SHA-256 hash-chained tamper-evident receipts. MCP server included. ([PyPI](https://pypi.org/project/sdcgovernance/))

### Commercial Platform

- **[SDCStudio](https://sdcstudio.axius-sdc.com)** v4.0.0 - Web application for AI-powered SDC model generation, schema export, and semantic enrichment

All SDC projects use **4.x.x** versioning where the MAJOR version (4) represents the current SDC generation.

### Two organizations, and what the line between them means

You will see work under two GitHub organizations. The split is deliberate and the axis is
stewardship, not licensing.

- **[SemanticDataCharter](https://github.com/SemanticDataCharter)** holds **the specification and its
  open reference implementation**: the reference model, the open component library, and the tools
  that validate and govern against it. This is the part intended to outlive any single company, and
  it is the part a foundation home would take. Everything here is Apache License 2.0. A repository
  that is temporarily private is unreleased, not proprietary.
- **[Axius-SDC](https://github.com/Axius-SDC)** holds the work of **Axius SDC, Inc.**, the company
  that maintains SDC: products, demos and commercial platforms. **Some of it is open source too**,
  for example [CordovaOS](https://github.com/Axius-SDC/CordovaOS). Licensing there is per repository;
  check the LICENSE file.

The short version: **this organization is the standard, the other is the company.** Contributions to
repositories here are covered by the
[Contributor License Agreement](https://github.com/SemanticDataCharter/.github/blob/main/CLA/README.md).

`AxiusSDC`, without the hyphen, is not an organization we use. If you find a link pointing at it,
it is a typo and we would be glad to hear about it.

## 25 Years of Engineering for This Moment

SDC was not built in response to the AI era. It was built in anticipation of it.

**Evolution Timeline:**
- **2000-2009**: FreePM/TORCH (open source healthcare applications)
- **2009-2017**: MLHIM (430 commits, 165+ citations, healthcare focus)
- **2012-2025**: S3Model (1,586 commits, domain-agnostic generalization)
- **2025-present**: SDC4 (commercial production platform)

**Lineage Validation (MLHIM and S3Model):**
- 12+ peer-reviewed papers (AMIA, JCI, JAMA, IEEE/ACM)
- 165+ citations on Google Scholar
- Applied in healthcare, research, and enterprise contexts

These attach to the predecessor projects. SDC4 inherits the modeling approach, not the citation record.

**Provenance:** The full development history from 2013 is preserved in a private archive, available for due diligence on request.

## Technology Stack

SDC aligns with the vocabularies of international standards:

**W3C Standards:**
- XML Schema 1.1 (structure)
- RDF 1.1 (semantics)
- OWL 2 (ontologies)
- SPARQL 1.1 (queries)
- SHACL (validation)

**ISO Standards:**
- ISO 11179 (metadata registries)
- ISO 20022 (financial messaging)
- ISO/IEC 21838 (top-level ontologies)
- ISO 21090 (healthcare data types)

**IETF Standards:**
- RFC 3986 (URIs)
- RFC 8259 (JSON)
- And more...

**OASIS Standards:**
- XACML 3.0 (governance decisions)

**OMG Standards:**
- DMN (decision tables)

**Total**: 24 international standards from 6 standards bodies

## Quick Start

### Convert a Form to an SDC Template

The fastest path from existing form to SDC model:

1. Open the [Form2SDCTemplate Colab notebook](https://colab.research.google.com/github/SemanticDataCharter/Form2SDCTemplate/blob/main/notebooks/form_to_template.ipynb)
2. Enter your free [Google AI API key](https://aistudio.google.com/apikey)
3. Upload a PDF, DOCX, or image form
4. Download the generated SDC markdown template
5. Upload to [SDCStudio](https://sdcstudio.axius-sdc.com) for processing

Or use the Python package:

```bash
pip install "form2sdc[gemini]"
```

```python
from form2sdc.analyzer import GeminiAnalyzer
from form2sdc.core import FormToTemplatePipeline
from pathlib import Path

analyzer = GeminiAnalyzer(api_key="YOUR_KEY")
pipeline = FormToTemplatePipeline(analyzer)
result = pipeline.process(Path("your_form.pdf"))

print(result.template)          # SDC markdown
print(result.validation.valid)  # True if valid
```

### Validate SDC Data

```bash
pip install sdcvalidator
```

```python
from sdcvalidator import SDC4Validator

validator = SDC4Validator('schema.xsd')
result = validator.validate('data.xml')

if result.is_valid:
    print("Valid!")
else:
    print(f"Structural errors: {len(result.structural_errors)}")
    print(f"Semantic errors: {len(result.semantic_errors)}")
```

### Govern SDC Data

```bash
pip install sdcgovernance
```

```python
from sdcgovernance import validate_governance, GovernanceEngine

# Primary API: validate governance content in an instance against its model
result = validate_governance("model.xsd", "instance.xml")
print(result.decision)       # Decision.PERMIT

# Stateful engine, for agents evaluating transitions across a session
engine = GovernanceEngine("model.xsd")
result = engine.evaluate_transition(current_state="draft", target_state="review")
print(result.decision)
print(result.receipt.receipt_hash)   # SHA-256 tamper-evident receipt
```

### Explore the Reference Model

```bash
git clone https://github.com/SemanticDataCharter/SDCRM.git
cd SDCRM
# See sdc4/schemas/sdc4.xsd (source of truth)
# See sdc4/specification/sdc4-specification.md
```

## Contributing

We welcome contributions to all SDC projects!

### Ways to Contribute

- **Code** - Implement features, fix bugs, improve performance
- **Documentation** - Write guides, improve examples, translate content
- **Testing** - Write tests, report bugs, verify fixes
- **Use Cases** - Share how you're using SDC
- **Feedback** - Suggest improvements, discuss architecture

### Getting Started

1. Read the [Contributing Guidelines](CONTRIBUTING.md)
2. Agree to the [Contributor License Agreement](CLA/README.md) before your first merge. You keep
   ownership of your work; see the CLA README for what it grants and why.
3. Check the [Code of Conduct](CODE_OF_CONDUCT.md)
4. Review the [Security Policy](SECURITY.md)
5. Find a project that interests you
6. Open an issue or PR

### Repository-Specific Guidelines

Each repository has its own CONTRIBUTING.md and CLAUDE.md files with specific guidance for that project.

## Security

We take security seriously. See our [Security Policy](SECURITY.md) for:
- Vulnerability reporting
- Security best practices
- Response timeline

**Report vulnerabilities**: security@axius-sdc.com

## Resources

- **Website**: [https://semanticdatacharter.com](https://semanticdatacharter.com)
- **Specification**: [sdc4-specification.md](https://github.com/SemanticDataCharter/SDCRM/blob/main/sdc4/specification/sdc4-specification.md)
- **Practitioners**: [https://axius-sdc.com/practitioners/](https://axius-sdc.com/practitioners/)
- **PyPI Packages**: [sdcvalidator](https://pypi.org/project/sdcvalidator/) | [sdcgovernance](https://pypi.org/project/sdcgovernance/) | [form2sdc](https://pypi.org/project/form2sdc/)
- **AI Instructions**: [ai.txt](https://semanticdatacharter.com/ai.txt)

## About

**Controlled and maintained by**: [Axius SDC, Inc.](https://axius-sdc.com)
**Contact**: contact@axius-sdc.com
**License**: Apache 2.0 (specification and open source tools)

**Founders**:
- Timothy W. Cook - Founder & CEO
- Dr. Luciana Tricai Cavalini, PhD - Co-Founder & Partner
- Dr. Nikki Shaw, PhD - Co-Founder & Partner

**Team**: International (US, Canada, Brazil), 40+ years combined experience

## Links

- **Website**: [semanticdatacharter.com](https://semanticdatacharter.com)
- **Company**: [axius-sdc.com](https://axius-sdc.com)
- **LinkedIn**: [Axius SDC](https://www.linkedin.com/company/axius-sdc)
- **Email**: contact@axius-sdc.com

## License

- **SDC Specification**: Apache 2.0
- **Open Source Libraries**: Apache 2.0
- **Trademarks**: "Semantic Data Charter" and "SDC" are trademarks of Axius SDC, Inc.

---

**The autonomous era needs deterministic data. The substrate is ready.**
