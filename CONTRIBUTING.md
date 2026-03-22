# Contributing to GitOps Capstone

Thank you for taking the time to contribute! This document outlines the standards and workflow expected for all contributions to this project. Please read it fully before opening a pull request.

---

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Before You Start](#before-you-start)
- [Branch Naming Convention](#branch-naming-convention)
- [Commit Message Convention](#commit-message-convention)
- [Code Style](#code-style)
- [Testing Requirements](#testing-requirements)
- [Pull Request Process](#pull-request-process)
- [CI Pipeline Requirements](#ci-pipeline-requirements)
- [What Not to Do](#what-not-to-do)

---

## Code of Conduct

This project is a learning environment. All contributors are expected to engage respectfully and constructively. Feedback on pull requests should be clear, specific, and kind.

---

## Before You Start

1. Check the Trello board for an available task in the **Backlog** column. Do not start work without a Trello card — every branch must reference one.
2. Assign yourself to the card before creating a branch.
3. If you want to suggest a new feature or fix a bug not on the board, open a GitHub Issue first to discuss it.
4. Follow the setup steps in [GETTING_STARTED.md](./GETTING_STARTED.md) to prepare your local environment.

---

## Branch Naming Convention

All branches must follow this format:

```
feature/TRELLO-###-short-description
```

**Examples:**
- `feature/TRELLO-005-add-multiply-endpoint`
- `feature/TRELLO-009-refactor-health-check`
- `feature/TRELLO-012-update-dependencies`

**Rules:**
- Always branch off the latest `main` (`git pull upstream main` first)
- Use lowercase and hyphens — no spaces, underscores, or camelCase
- Keep descriptions short but meaningful
- Never commit directly to `main`

---

## Commit Message Convention

Every commit message must follow this format:

```
[TRELLO-###] Short description of what was changed
```

**Examples:**
- `[TRELLO-005] Add multiply endpoint to app.py`
- `[TRELLO-003] Add 8th test for missing keys in sum endpoint`
- `[TRELLO-002] Refactor CI workflow to use job matrix`

**Rules:**
- The Trello number must match the branch you are working on
- Use the imperative mood — "Add", "Fix", "Update", not "Added" or "Adding"
- Keep the subject line under 72 characters
- If more detail is needed, add a blank line after the subject and write a longer body

---

## Code Style

This project enforces **PEP 8** compliance using **flake8**. Before pushing any code:

```bash
flake8 app.py test_app.py
```

No output means no violations. Common rules to keep in mind:

- Lines must not exceed **88 characters**
- Use 4 spaces for indentation — never tabs
- Leave two blank lines between top-level functions
- Avoid unused imports
- Keep function names in `snake_case`

If flake8 reports any errors, fix them before committing. The CI pipeline will block your PR if lint fails.

---

## Testing Requirements

All contributions that change `app.py` must include corresponding tests in `test_app.py`.

```bash
pytest test_app.py -v
```

**Requirements:**
- All existing tests must continue to pass — do not remove or modify passing tests unless the endpoint behaviour itself has changed
- New endpoints require at least one test for the expected case and one for an edge case (e.g., missing or empty input)
- Tests must use the Flask `test_client()` fixture pattern already established in `test_app.py`
- Do not introduce `print()` statements or debug code in production files

---

## Pull Request Process

1. Ensure your branch is up to date with `main` before opening a PR:

   ```bash
   git checkout main
   git pull upstream main
   git checkout feature/TRELLO-###-your-branch
   git merge main
   ```

2. Verify all checks pass locally:

   ```bash
   flake8 app.py test_app.py
   pytest test_app.py -v
   ```

3. Push your branch:

   ```bash
   git push origin feature/TRELLO-###-your-branch
   ```

4. Open a pull request on GitHub against `main` with:
   - **Title:** `[TRELLO-###] Brief description`
   - **Description:** What was changed, why, and any relevant notes for the reviewer
   - **Reviewer:** Assign at least one reviewer from the right panel

5. Wait for the CI pipeline to complete. If it fails, fix the issue on the same branch — the pipeline will re-run on the next push.

6. Do not merge your own PR. A reviewer must approve and merge it.

---

## CI Pipeline Requirements

The GitHub Actions CI pipeline runs automatically on every push and pull request. It will:

1. Install all dependencies from `requirements.txt`
2. Run `flake8 app.py test_app.py`
3. Run `pytest test_app.py -v`

**A PR cannot be merged unless all three steps pass.** If any step fails, the PR will show a red X. Click "Details" next to the failing check to read the logs and identify the issue.

---

## What Not to Do

- Do **not** push directly to `main`
- Do **not** open a PR without a Trello card reference
- Do **not** merge your own pull request
- Do **not** disable or skip flake8 rules with `# noqa` comments without a documented reason
- Do **not** commit secrets, API keys, credentials, or `.env` files — these are in `.gitignore` for a reason
- Do **not** leave commented-out code in your final commit

---

If you are unsure about anything, open a GitHub Issue or ask before submitting a PR. Good contributions start with good communication.

