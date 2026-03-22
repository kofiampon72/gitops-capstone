# Getting Started — New Contributor Guide

> You should be able to make your first commit in under 1 hour.

This guide walks you through setting up your local development environment, running the app, passing all tests, and submitting your first pull request.

---

## Prerequisites

Before you begin, make sure the following are installed on your machine:

| Tool | Version | Download |
|---|---|---|
| Python | 3.10+ | https://www.python.org/downloads/ |
| Git | Latest | https://git-scm.com/ |
| pip | Bundled with Python | — |

---

## Step 1 — Configure Git (5 minutes)

If this is your first time using Git on this machine, set your identity:

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

---

## Step 2 — Fork and Clone the Repository (5 minutes)

1. Go to https://github.com/kofiampon72/gitops-capstone
2. Click **Fork** (top right) to create your own copy
3. Clone your fork locally:

```bash
git clone https://github.com/YOUR_USERNAME/gitops-capstone.git
cd gitops-capstone
```

4. Add the original repo as an upstream remote so you can pull future updates:

```bash
git remote add upstream https://github.com/kofiampon72/gitops-capstone.git
```

---

## Step 3 — Install Dependencies (2 minutes)

```bash
pip install -r requirements.txt
```

This installs `flask`, `pytest`, and `flake8`.

---

## Step 4 — Run the Application (1 minute)

```bash
python app.py
```

The app will start on `http://localhost:5000`. You can test the health endpoint immediately:

```bash
curl http://localhost:5000/health
# Expected: {"status": "UP"}
```

Or test the other endpoints:

```bash
# Sum endpoint
curl -X POST http://localhost:5000/sum \
  -H "Content-Type: application/json" \
  -d '{"a": 5, "b": 10}'
# Expected: {"result": 15}

# Reverse string endpoint
curl -X POST http://localhost:5000/reverse-string \
  -H "Content-Type: application/json" \
  -d '{"text": "hello"}'
# Expected: {"result": "olleh"}
```

---

## Step 5 — Run the Tests (2 minutes)

```bash
pytest test_app.py -v
```

You should see **8 tests, all PASSED**. If any tests fail, stop here — check your Python version and re-run `pip install -r requirements.txt` before continuing.

---

## Step 6 — Run the Linter (1 minute)

```bash
flake8 app.py test_app.py
```

No output means no lint errors. This check **must pass** before you open a pull request. If you see errors, fix them before continuing.

> Keep all lines under 88 characters to avoid `E501` line-too-long errors.

---

## Step 7 — Create a Feature Branch (5 minutes)

All work must be done on a feature branch. **Never commit directly to `main`.**

```bash
# First, make sure your main is up to date
git checkout main
git pull upstream main

# Create your feature branch using the Trello task number
git checkout -b feature/TRELLO-###-short-description
```

Replace `###` with your Trello card number and `short-description` with a brief lowercase description (e.g., `feature/TRELLO-005-add-multiply-endpoint`).

---

## Step 8 — Make Your Changes

Make your code changes, then verify everything still passes:

```bash
flake8 app.py test_app.py   # Must show no errors
pytest test_app.py -v       # All tests must pass
```

---

## Step 9 — Commit and Push (2 minutes)

```bash
git add .
git commit -m "[TRELLO-###] Your descriptive commit message"
git push origin feature/TRELLO-###-short-description
```

**Commit message format:** Always prefix with the Trello task number in square brackets, e.g., `[TRELLO-005] Add multiply endpoint`.

---

## Step 10 — Open a Pull Request (5 minutes)

1. Go to your fork on GitHub
2. Click **"Compare & pull request"** (GitHub will prompt you after a push)
3. Set the **base repository** to `kofiampon72/gitops-capstone` and **base branch** to `main`
4. Title your PR using the same format: `[TRELLO-###] Brief description`
5. Fill in the description — what you changed and why
6. Click **"Create pull request"**
7. Request a reviewer from the right panel

---

## Step 11 — After CI Runs

The GitHub Actions CI pipeline will automatically run on your PR. Wait for all checks to complete:

- **Green checkmarks** — your PR is ready for review
- **Red X** — read the failing step's logs, fix the issue, commit, and push again (the CI will re-run automatically)

Once the CI is green and a reviewer approves, your PR will be merged into `main`.

---

## Troubleshooting

| Problem | Solution |
|---|---|
| `ModuleNotFoundError: flask` | Run `pip install -r requirements.txt` |
| `flake8` reports `E501 line too long` | Keep all lines under 88 characters |
| `pytest` shows `FAILED` | Read the error message carefully — check the assert values |
| `git push` rejected | Make sure you are on a feature branch, not on `main` |
| CI fails on GitHub | Click the red X → "Details" to read the full logs |
| `git pull` has merge conflicts | Resolve conflicts locally, commit the resolution, then push |

---

If you get stuck, open a GitHub Issue and describe the problem clearly.

