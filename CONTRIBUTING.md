# Contributing to Ainfera

Thank you for your interest in contributing to Ainfera.

## Getting Started

1. Fork the repository
2. Clone your fork
3. Create a feature branch: `git checkout -b feat/my-feature`
4. Make your changes
5. Run tests: `make test`
6. Run lint: `make lint`
7. Commit with conventional commits: `git commit -m "feat: add new feature"`
8. Push and create a Pull Request

## Commit Convention

We use [Conventional Commits](https://www.conventionalcommits.org/):

- `feat:` — New feature
- `fix:` — Bug fix
- `docs:` — Documentation
- `chore:` — Maintenance
- `refactor:` — Code restructuring
- `test:` — Tests
- `ci:` — CI/CD changes

## Development Setup

### CLI
```bash
cd cli
pip install -e ".[dev]"
ainfera --version
python -m pytest tests/
```

### Python SDK
```bash
cd sdk-python
pip install -e ".[dev]"
python -m pytest tests/
```

## Code Style

- **Python**: ruff formatter + linter, mypy strict
- **All**: type hints required, no `any` types

## Questions?

Open a Discussion or reach out at hello@ainfera.ai.

---

© 2026 Ainfera
