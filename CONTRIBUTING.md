# Contributing to TokenGuard

Thank you for your interest in contributing to **TokenGuard**! We welcome security signature additions, bug reports, performance improvements, and pull requests.

---

## 🛠️ Development Setup

TokenGuard is built with **zero external runtime dependencies** using the Python standard library. It supports Python 3.9 through 3.14.

```bash
# Clone the repository
git clone https://github.com/umutgungorr/tokenguard.git
cd tokenguard

# Install editable development build with uv
uv pip install -e .
```

---

## 🧪 Running Tests & Quality Checks

We maintain a strict 100% test pass rate across all operating systems and Python versions (3.9–3.14):

```bash
# Run full pytest suite
uv run --with pytest pytest contract_tests tests -v

# Run Ruff linter
uv run --with ruff ruff check .

# Run Ruff format check
uv run --with ruff ruff format --check .
```

---

## 🔍 Adding New Secret Detection Signatures

1. Define the regex pattern, severity, confidence, and actionable remediation in `src/tokenguard/rules.py` within `RULES`.
2. Add corresponding unit tests in `tests/test_tokenguard.py` (using split string literals so self-scans stay clean).
3. Verify Shannon entropy interaction and ensure zero false positives on normal source code syntax.
4. Ensure `dependencies = []` remains untouched in `pyproject.toml`.

---

## 📜 Code of Conduct

Please review and respect our [Code of Conduct](CODE_OF_CONDUCT.md) in all community interactions.
