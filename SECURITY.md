# Security Policy

## Reporting a Vulnerability

We take the security of the Semantic Data Charter (SDC4) ecosystem seriously. If you discover a security vulnerability, please report it responsibly.

### How to Report

**Email**: security@axius-sdc.com

**Please include:**
- Description of the vulnerability
- Steps to reproduce the issue
- Potential impact and severity assessment
- Affected versions/components
- Suggested fix (if available)
- Your contact information

**Do NOT:**
- Open a public GitHub issue for security vulnerabilities
- Disclose the vulnerability publicly until we've had a chance to address it
- Exploit the vulnerability beyond what's necessary to demonstrate it

### Response Timeline

- **Initial Response**: Within 48 hours
- **Status Update**: Within 7 days
- **Fix Timeline**: Depends on severity (see below)
- **Public Disclosure**: Coordinated with reporter

### Severity Levels

| Severity | Description | Response Time |
|----------|-------------|---------------|
| **Critical** | Remote code execution, authentication bypass, data breach | 24-48 hours |
| **High** | Privilege escalation, SQL injection, XSS | 1 week |
| **Medium** | Information disclosure, DoS | 2 weeks |
| **Low** | Minor issues with limited impact | 4 weeks |

### What to Expect

1. **Acknowledgment** - We'll confirm receipt within 48 hours
2. **Investigation** - We'll assess the vulnerability and its impact
3. **Fix Development** - We'll develop and test a patch
4. **Disclosure** - We'll coordinate public disclosure with you
5. **Credit** - You'll be credited in the security advisory (if desired)
6. **Release** - We'll release the fix and publish an advisory

## Supported Versions

Security updates are provided for the following versions:

### Core Repositories

| Project | Version | Supported |
| ------- | ------- | --------- |
| **SDCRM** | 4.0.x | ✅ Yes |
| **sdc-xml2graph** | 4.0.x | ✅ Yes (Q1-2026) |
| **SDCObsidianTemplate** | 4.0.x | ✅ Yes |

### Validation Libraries

| Project | Version | Supported |
| ------- | ------- | --------- |
| **sdcvalidator (Python)** | 4.0.x | ✅ Yes |
| **sdcvalidatorJS (TypeScript)** | 4.0.x | ✅ Yes |

### Commercial Platform

| Project | Version | Supported |
| ------- | ------- | --------- |
| **SDCStudio** | 4.0.x | ✅ Yes (proprietary support) |

**Note**: All SDC4 projects use 4.x.x versioning where MAJOR version (4) = SDC generation.

## Security Best Practices

### For Users

#### XML Processing

All SDC4 projects that process XML must protect against common vulnerabilities:

**1. XML External Entity (XXE) Attacks**

```python
# Python (lxml)
from lxml import etree

parser = etree.XMLParser(
    resolve_entities=False,  # Disable external entities
    no_network=True,         # Disable network access
    dtd_validation=False,    # Disable DTD validation
    load_dtd=False          # Don't load DTD
)
tree = etree.parse('data.xml', parser)
```

```typescript
// TypeScript (@xmldom/xmldom)
import { DOMParser } from '@xmldom/xmldom';

const parser = new DOMParser({
  locator: {},
  errorHandler: {
    warning: (w) => console.warn(w),
    error: (e) => console.error(e),
    fatalError: (e) => { throw e; }
  }
});

// @xmldom/xmldom is safe by default (no external entity resolution)
const doc = parser.parseFromString(xmlString, 'text/xml');
```

**2. Billion Laughs Attack (XML Bomb)**

Set resource limits:

```python
MAX_FILE_SIZE = 100 * 1024 * 1024  # 100MB

def parse_safely(xml_path: str):
    import os
    if os.path.getsize(xml_path) > MAX_FILE_SIZE:
        raise ValueError("File too large")

    parser = etree.XMLParser(
        huge_tree=False,         # Limit tree size
        resolve_entities=False   # Prevent entity expansion
    )
    return etree.parse(xml_path, parser)
```

**3. XPath Injection**

Never use user input directly in XPath expressions:

```python
# ❌ DANGEROUS
user_input = request.GET['name']
xpath = f"//component[@name='{user_input}']"

# ✅ SAFE - Sanitize and validate
safe_name = re.sub(r'[^\w\s-]', '', user_input)
xpath = f"//component[@name=$name]"
results = tree.xpath(xpath, name=safe_name)
```

#### Database Security

**1. SQL Injection Prevention**

Always use parameterized queries:

```python
# ❌ DANGEROUS
cursor.execute(f"SELECT * FROM models WHERE id = '{user_id}'")

# ✅ SAFE
cursor.execute("SELECT * FROM models WHERE id = %s", (user_id,))
```

**2. SPARQL Injection Prevention**

```python
from rdflib import Graph, Literal
from rdflib.plugins.sparql import prepareQuery

# ❌ DANGEROUS
user_input = "John'; DROP ALL; #"
query_string = f"""
    SELECT ?s WHERE {{
        ?s sdc:value "{user_input}"
    }}
"""

# ✅ SAFE - Parameterized query
query = prepareQuery("""
    SELECT ?s WHERE {
        ?s sdc:value ?input
    }
""")
results = graph.query(query, initBindings={'input': Literal(user_input)})
```

#### Dependency Security

**Python Projects:**

```bash
# Check for known vulnerabilities
pip-audit

# Update dependencies
pip install --upgrade sdcvalidator

# Verify checksums
pip install sdcvalidator==4.0.1 --require-hashes
```

**TypeScript Projects:**

```bash
# Check for known vulnerabilities
npm audit

# Fix automatically when possible
npm audit fix

# Update dependencies
npm update sdcvalidatorjs
```

#### Secrets Management

**Never commit:**
- API keys
- Database credentials
- Private keys
- Passwords
- OAuth tokens

**Use:**
- Environment variables (.env files in .gitignore)
- Secret management services (AWS Secrets Manager, Azure Key Vault, etc.)
- Git hooks to prevent accidental commits

```bash
# Pre-commit hook to check for secrets
pip install detect-secrets
detect-secrets scan > .secrets.baseline
```

### For Contributors

#### Secure Coding Practices

**1. Input Validation**

Validate all user input:

```python
def validate_component_type(component_type: str) -> bool:
    """Validate component type against allowed list."""
    ALLOWED_TYPES = {
        'XdString', 'XdBoolean', 'XdCount', 'XdQuantity',
        'XdTemporal', 'XdFile', 'XdLink', 'XdOrdinal'
    }
    return component_type in ALLOWED_TYPES

if not validate_component_type(user_component_type):
    raise ValueError(f"Invalid component type: {user_component_type}")
```

**2. Output Encoding**

Encode output to prevent injection:

```python
import html

# HTML output
safe_output = html.escape(user_input)

# XML output
from xml.sax.saxutils import escape
safe_xml = escape(user_input)
```

**3. Error Handling**

Don't leak sensitive information in errors:

```python
# ❌ DANGEROUS - Exposes file paths
try:
    with open('/var/sdc/secret/config.yaml') as f:
        config = f.read()
except FileNotFoundError as e:
    raise Exception(f"Config file not found: {e}")

# ✅ SAFE - Generic error message
try:
    with open(config_path) as f:
        config = f.read()
except FileNotFoundError:
    raise Exception("Configuration file not found")
```

**4. Authentication & Authorization**

```python
# Check authentication
if not request.user.is_authenticated:
    raise PermissionDenied("Authentication required")

# Check authorization
if not request.user.has_perm('rm.view_datamodel'):
    raise PermissionDenied("Insufficient permissions")
```

#### Code Review Checklist

Before submitting a PR, verify:

- [ ] **Input validation** - All user input is validated
- [ ] **Output encoding** - Output is properly encoded
- [ ] **Authentication** - Protected endpoints require authentication
- [ ] **Authorization** - Users can only access authorized resources
- [ ] **Error handling** - Errors don't leak sensitive information
- [ ] **Secrets** - No hardcoded credentials or API keys
- [ ] **Dependencies** - All dependencies are up to date
- [ ] **Tests** - Security tests are included
- [ ] **Documentation** - Security considerations are documented

## Security Features by Project

### sdcvalidator (Python)

**Security Features:**
- Safe XML parsing (lxml with secure defaults)
- ExceptionalValue recovery (preserves invalid data safely)
- Schema validation before processing
- Resource limits on file size and complexity

**Security Testing:**
```bash
# Run security tests
pytest tests/security/

# Check dependencies
pip-audit

# Scan for secrets
detect-secrets scan
```

### sdcvalidatorJS (TypeScript)

**Security Features:**
- Safe XML parsing (@xmldom/xmldom with no external entities)
- TypeScript strict mode for type safety
- ESLint security rules
- npm audit integration

**Security Testing:**
```bash
# Run security tests
npm test

# Check dependencies
npm audit

# Fix vulnerabilities
npm audit fix
```

### SDCStudio (Django)

**Security Features:**
- CSRF protection enabled
- SQL injection protection (Django ORM)
- XSS prevention (template auto-escaping)
- Secure password hashing (Argon2)
- HTTPS enforcement in production
- Content Security Policy headers
- Rate limiting on API endpoints

**Security Testing:**
```bash
# Django security checks
python manage.py check --deploy

# Dependency scanning
pip-audit

# SAST scanning
bandit -r src/
```

### SDCRM (Schemas)

**Security Considerations:**
- Schema validation to prevent malformed data
- Namespace URI validation
- CUID validation for identifiers
- XSD 1.1 assertions for constraints

## Automated Security Scanning

All repositories include automated security scanning:

### GitHub Actions

```yaml
# .github/workflows/security.yml
name: Security

on:
  push:
    branches: [main]
  pull_request:
  schedule:
    - cron: '0 0 * * 1'  # Weekly

jobs:
  dependency-scan:
    # pip-audit, npm audit, etc.

  codeql:
    # GitHub CodeQL analysis

  secret-scan:
    # Gitleaks for secret detection
```

### Dependency Scanning

- **Python**: pip-audit, safety
- **TypeScript**: npm audit, Snyk
- **GitHub**: Dependabot alerts

### Code Analysis

- **Python**: Bandit (SAST), CodeQL
- **TypeScript**: ESLint security rules, CodeQL
- **All**: GitHub Secret Scanning

## Security Advisories

Published security advisories are available at:
- **GitHub**: [Security Advisories](https://github.com/SemanticDataCharter/SDCRM/security/advisories)
- **Website**: [https://semanticdatacharter.com/security](https://semanticdatacharter.com/security)

Subscribe to security notifications:
- **GitHub**: Watch → Custom → Security alerts
- **Email**: Subscribe at contact@axius-sdc.com

## Disclosure Policy

### Coordinated Disclosure

We practice responsible disclosure:

1. **Report received** - Acknowledgment within 48 hours
2. **Investigation** - Assess severity and impact
3. **Fix development** - Create and test patch
4. **Embargo period** - Typically 90 days
5. **Public disclosure** - Coordinated with reporter
6. **Credit** - Reporter credited (if desired)

### Public Disclosure

Security advisories will include:
- **Vulnerability description**
- **Affected versions**
- **Severity rating** (CVSS score)
- **Mitigation steps**
- **Fixed versions**
- **Credit to reporter**

## Bug Bounty

We currently do not have a formal bug bounty program, but we:
- Credit security researchers in advisories
- Provide attribution in release notes
- Consider donations for significant findings

Contact security@axius-sdc.com to discuss.

## Security Resources

- **OWASP Top 10**: [https://owasp.org/Top10/](https://owasp.org/Top10/)
- **CWE Database**: [https://cwe.mitre.org/](https://cwe.mitre.org/)
- **NIST NVD**: [https://nvd.nist.gov/](https://nvd.nist.gov/)
- **GitHub Security**: [https://github.com/security](https://github.com/security)

## Contact

- **Security Issues**: security@axius-sdc.com
- **General Security Questions**: Use GitHub Discussions
- **PGP Key**: Available upon request

---

**Security is everyone's responsibility.** Thank you for helping keep SDC4 secure! 🔒

*Last Updated: November 2025*
