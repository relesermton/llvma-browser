# Contributing to LLVMA

Thank you for your interest in improving LLVMA! We welcome all contributions, including bug reports, documentation improvements, crawler connectors, UI enhancements, and core engine optimizations.

---

## Code of Conduct

By participating in this project, you agree to treat all contributors with respect, courtesy, and professionalism. Harassment or toxic behavior will not be tolerated.

---

## How Can I Contribute?

- **Report Bugs**: Submit detailed issue reports with steps to reproduce.
- **Request Features**: Share ideas for new search integrations, ranking algorithms, or LLM providers.
- **Submit PRs**: Fix issues, add test coverage, improve documentation, or implement new features.

---

## Development Setup

### 1. Fork and Clone

1. Fork the repository on GitHub.
2. Clone your fork locally:
   ```bash
   git clone https://github.com/<your-username>/llvma.git
   cd llvma
Add the upstream remote:
git remote add upstream https://github.com/llvma/llvma.git
2. Environment Setup
LLVMA consists of two primary layers:

Backend (Core Engine & API)
cd backend
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements-dev.txt
Frontend (Web Interface)
cd frontend
npm install
Branching & Commit Guidelines
Branch Naming
Create a dedicated branch for each change:

feature/add-searxng-connector
fix/query-parser-encoding
docs/update-docker-guide
Conventional Commits
We follow the Conventional Commits specification:

feat: A new feature (e.g., feat: support hybrid dense/sparse reranking)
fix: A bug fix (e.g., fix: handle empty response from local Ollama instance)
docs: Documentation only changes
refactor: Code changes that neither fix a bug nor add a feature
test: Adding or updating tests
chore: Build process or auxiliary tool changes
Quality Standards
Before opening a pull request, verify that your changes pass all linters and tests.

Backend Checks
cd backend

# Format & Lint
ruff check .
black --check .

# Run Tests
pytest tests/
Frontend Checks
cd frontend

# Format & Lint
npm run lint
npm run format:check

# Type check
npm run typecheck
Pull Request Process
Keep it focused: One bug fix or feature per pull request.
Sync upstream: Rebase your branch onto the latest upstream/main before submitting:
git fetch upstream
git rebase upstream/main
Include tests: Add unit or integration tests for any new functionality or bug fixes.
Update docs: If your change modifies an API endpoint, config variable, or workflow, update the documentation in README.md or /docs.
Open the PR: Provide a clear summary of your changes and reference any related issues (Fixes #123).
Need Help?
Start a discussion in the GitHub Discussions tab.
If you find a security vulnerability, please do not open a public issue. Email security concerns to security@llvma.dev (or see SECURITY.md).
