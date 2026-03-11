# Semantic Data Charter™

### The Blueprint for Trusted Data

The **Semantic Data Charter (SDC4)** is an open specification for creating self-describing, semantically rich data models that work seamlessly across systems and languages.

> **This organization and all repositories within it are controlled and maintained by [Axius SDC, Inc.](https://axius-sdc.github.io)**

## 🌟 Vision

**Make data trustworthy, interoperable, and permanent.**

We believe the foundation of data trust should be:
- **Open** - Built on international standards, not proprietary lock-in
- **Accessible** - Language-agnostic, enabling global collaboration
- **Governed** - Built-in lineage and provenance for accountability
- **Permanent** - CUID-based immutability for long-term data integrity

## 🔑 Core Principles

### Three Pillars of SDC4

1. **Enforce Governance** - Built-in lineage and provenance tracking
2. **Embed Meaning** - Semantic interoperability via RDF/OWL
3. **Mandate Quality** - Validation rules and quality constraints

## 🏗️ What is SDC4?

Think of it as: **"Protocol Buffers with semantics and governance"**

SDC4 combines:
- **Structure** (like Protocol Buffers) - XML Schema 1.1 for data types and constraints
- **Semantics** (like RDF/OWL) - Meaning and relationships
- **Validation** (like SHACL) - Quality rules and business logic
- **Governance** - Lineage, provenance, and audit trails
- **Packaging** - Self-contained, queryable data packages

**Result**: Data that is self-describing, semantically rich, and audit-ready.

## 🚀 Key Features

- ✅ **Language Agnostic** - Model in Portuguese, French, Japanese, Spanish, etc.
- ✅ **Standards-Based** - Built on 16+ W3C, ISO, and IETF standards
- ✅ **AI Governance** - Built-in lineage for trustworthy, explainable AI
- ✅ **Namespace Versioning** - CUIDs for immutable, evolvable components
- ✅ **Multi-Format Export** - RDF, OWL, SHACL, FHIR, GraphQL, JSON, GQL

## 🌍 Use Cases

- **Enterprise Data Integration** - Canonical models for multi-system environments
- **AI Governance** - Data packages with automatic lineage for trustworthy AI
- **Cross-Border Exchange** - Semantic interoperability without translation
- **Regulatory Compliance** - Built-in audit trails and provenance
- **Legacy Modernization** - Bridge between old and new systems

## 📦 SDC4 Ecosystem

### Core Repositories

- **[SDCRM](https://github.com/SemanticDataCharter/SDCRM)** v4.0.0 - Reference model, schemas, and specification
- **[sdc-xml2graph](https://github.com/SemanticDataCharter/sdc-xml2graph)** v4.0.0 - Transform SDC4 XML to knowledge graphs (Q1-2026)

### Template Creation

- **[Form2SDCTemplate](https://github.com/SemanticDataCharter/Form2SDCTemplate)** v4.4.0 - Convert PDF, DOCX, and image forms into SDC4 templates using Gemini AI. Available as a [Python package](https://pypi.org/project/form2sdc/), [Google Colab notebook](https://colab.research.google.com/github/SemanticDataCharter/Form2SDCTemplate/blob/main/notebooks/form_to_template.ipynb), or LLM instruction file.
- **[SDCObsidianTemplate](https://github.com/SemanticDataCharter/SDCObsidianTemplate)** v4.3.0 - Interactive Obsidian Templater plugin for building SDC4 markdown templates with guided prompts, domain-aware defaults, and SDC4 participation model support.

### Validation & Tools

- **[sdcvalidator (Python)](https://github.com/SemanticDataCharter/sdcvalidator)** v4.1.0 - SDC4 structural validator with two-tier error classification ([PyPI](https://pypi.org/project/sdcvalidator/))

### Commercial Platform

- **[SDCStudio](https://sdcstudio.axius-sdc.com)** v4.0.0 - Web application for AI-powered SDC4 model generation, schema export, and semantic enrichment (60-day free trial)

All SDC4 projects use **4.x.x** versioning where the MAJOR version (4) represents the SDC generation.

## 🔬 15+ Years of Research Foundation

SDC4 is not a new idea—it's the commercialization of 15+ years of validated research:

**Evolution Timeline:**
- **2000-2009**: FreePM/TORCH (open source healthcare applications)
- **2009-2017**: MLHIM (430 commits, 165+ citations, healthcare focus)
- **2012-2025**: S3Model (1,586 commits, domain-agnostic generalization)
- **2025-present**: SDC4 (commercial production platform)

**Academic Validation:**
- 12+ peer-reviewed papers (AMIA, JCI, JAMA, IEEE/ACM)
- 165+ citations on Google Scholar
- Proven in healthcare, research, and enterprise contexts

**Verification:** [Historical Archive](https://github.com/Axius-SDC/historical-archive) - 4.2GB, 76,313 files, full Git history (2013-2025)

## 🛠️ Technology Stack

SDC4 is built on international standards:

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

**Total**: 16+ international standards

## 💻 Quick Start

### Convert a Form to an SDC4 Template

The fastest path from existing form to SDC4 model:

1. Open the [Form2SDCTemplate Colab notebook](https://colab.research.google.com/github/SemanticDataCharter/Form2SDCTemplate/blob/main/notebooks/form_to_template.ipynb)
2. Enter your free [Google AI API key](https://aistudio.google.com/apikey)
3. Upload a PDF, DOCX, or image form
4. Download the generated SDC4 markdown template
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

print(result.template)          # SDC4 markdown
print(result.validation.valid)  # True if valid
```

### Validate SDC4 Data

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

### Explore the Reference Model

```bash
git clone https://github.com/SemanticDataCharter/SDCRM.git
cd SDCRM
# See sdc4/schemas/sdc4.xsd (source of truth)
# See sdc4/specification/sdc4-specification.md
```

## 🤝 Contributing

We welcome contributions to all SDC4 projects!

### Ways to Contribute

- **Code** - Implement features, fix bugs, improve performance
- **Documentation** - Write guides, improve examples, translate content
- **Testing** - Write tests, report bugs, verify fixes
- **Use Cases** - Share how you're using SDC4
- **Feedback** - Suggest improvements, discuss architecture

### Getting Started

1. Read the [Contributing Guidelines](CONTRIBUTING.md)
2. Check the [Code of Conduct](CODE_OF_CONDUCT.md)
3. Review the [Security Policy](SECURITY.md)
4. Find a project that interests you
5. Open an issue or PR

### Repository-Specific Guidelines

Each repository has its own CONTRIBUTING.md and CLAUDE.md files with specific guidance for that project.

## 🔒 Security

We take security seriously. See our [Security Policy](SECURITY.md) for:
- Vulnerability reporting
- Security best practices
- Response timeline

**Report vulnerabilities**: security@axius-sdc.com

## 📚 Resources

- **Website**: [https://semanticdatacharter.com](https://semanticdatacharter.com)
- **Specification**: [sdc4-specification.md](https://github.com/SemanticDataCharter/SDCRM/blob/main/sdc4/specification/sdc4-specification.md)
- **PyPI Packages**: [sdcvalidator](https://pypi.org/project/sdcvalidator/) | [form2sdc](https://pypi.org/project/form2sdc/)
- **Historical Archive**: [GitHub](https://github.com/Axius-SDC/historical-archive)
- **AI Instructions**: [ai.txt](https://semanticdatacharter.com/ai.txt)

## 🏢 About

**Controlled and maintained by**: [Axius SDC, Inc.](https://axius-sdc.github.io)
**Contact**: contact@axius-sdc.com
**License**: Apache 2.0 (specification and open source tools)

**Founders**:
- Timothy W. Cook - Founder & CEO
- Dr. Luciana Tricai Cavalini, PhD - Co-Founder & Partner
- Dr. Nikki Shaw, PhD - Co-Founder & Partner

**Team**: International (US, Canada, Brazil), 40+ years combined experience

## 🌐 Links

- **Website**: [semanticdatacharter.com](https://semanticdatacharter.com)
- **Company**: [axius-sdc.com](https://axius-sdc.com)
- **LinkedIn**: [Axius SDC](https://www.linkedin.com/company/axius-sdc)
- **Email**: contact@axius-sdc.com

## 📄 License

- **SDC4 Specification**: Apache 2.0
- **Open Source Libraries**: Apache 2.0
- **Trademarks**: "Semantic Data Charter" and "SDC4" owned by Axius SDC, Inc.

---

**Building the future of trusted data, one semantic model at a time.** 🚀

*Last Updated: February 2026*
