# GitOps Capstone Project

A GitOps-driven CI/CD capstone project. This project demonstrates real-world GitOps practices using a Python Flask REST API, automated testing with pytest, code quality enforcement with flake8, and a fully automated CI pipeline powered by GitHub Actions.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Tech Stack](#tech-stack)
- [Repository Structure](#repository-structure)
- [API Endpoints](#api-endpoints)
- [CI/CD Pipeline](#cicd-pipeline)
- [Running Locally](#running-locally)
- [Running Tests](#running-tests)
- [Branch & Workflow Strategy](#branch--workflow-strategy)
- [Contributing](#contributing)
- [Author](#author)

---

## Project Overview

This project applies GitOps principles to manage and automate the software delivery lifecycle of a simple Flask REST API. Every change to the codebase goes through:

1. A feature branch created from a Trello task
2. Automated linting (flake8) and testing (pytest) via GitHub Actions
3. A pull request review and merge into `main`

The goal is to demonstrate proficiency in CI/CD pipeline design, test-driven development, and GitOps workflows — skills central to a Junior DevOps / Cloud Engineer role.

---

## Tech Stack

| Layer | Tool |
|---|---|
| Application | Python 3.10+, Flask |
| Testing | pytest |
| Linting | flake8 |
| CI/CD | GitHub Actions |
| Version Control | Git / GitHub |
| Task Management | Trello |

---

## Repository Structure

```
gitops-capstone/
├── .github/
│   └── workflows/
│       └── ci.yml          # GitHub Actions CI pipeline
├── app.py                  # Flask application with REST endpoints
├── test_app.py             # pytest test suite (8 tests)
├── requirements.txt        # Python dependencies
├── .gitignore
├── GETTING_STARTED.md      # Setup guide for new contributors
├── CONTRIBUTING.md         # Contribution guidelines
└── README.md               # This file
```

---

## API Endpoints

The Flask app exposes three endpoints:

### `GET /health`
Returns the health status of the application.

**Response:**
```json
{ "status": "UP" }
```

---

### `POST /sum`
Accepts two numbers and returns their sum.

**Request body:**
```json
{ "a": 5, "b": 10 }
```

**Response:**
```json
{ "result": 15 }
```

> Missing keys default to `0`.

---

### `POST /reverse-string`
Accepts a string and returns it reversed.

**Request body:**
```json
{ "text": "hello" }
```

**Response:**
```json
{ "result": "olleh" }
```

---

## CI/CD Pipeline

The GitHub Actions CI pipeline (`.github/workflows/ci.yml`) runs automatically on every push and pull request to the `main` branch. It performs the following steps:

1. **Checkout** — clones the repository
2. **Set up Python** — installs Python 3.10+
3. **Install dependencies** — runs `pip install -r requirements.txt`
4. **Lint** — runs `flake8 app.py test_app.py`
5. **Test** — runs `pytest test_app.py -v`

All steps must pass before a pull request can be merged into `main`.

---

## Running Locally

```bash
# 1. Clone the repository
git clone https://github.com/kofiampon72/gitops-capstone.git
cd gitops-capstone

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run the Flask app
python app.py
```

---

## Running Tests

```bash
# Run all tests with verbose output
pytest test_app.py -v
```

All 8 tests should return `PASSED`. To also run the linter:

```bash
flake8 app.py test_app.py
```

No output from flake8 means no lint errors.

---

## Branch & Workflow Strategy

This project follows a Trello-linked feature branch workflow:

```
main  ←  feature/TRELLO-###-short-description
```

- All work is done on feature branches, never directly on `main`
- Branch names reference the Trello task number (e.g., `feature/TRELLO-003-Add-8th-Test`)
- Commit messages follow the format: `[TRELLO-###] Descriptive message`
- Pull requests are opened against `main` and must pass CI before merging

See [CONTRIBUTING.md](./CONTRIBUTING.md) and [GETTING_STARTED.md](./GETTING_STARTED.md) for full details.

---

## Contributing

Contributions are welcome! Please read [CONTRIBUTING.md](./CONTRIBUTING.md) before submitting a pull request.

---

## Author

**Konadu Kofi Amponsah**
Junior DevOps / Cloud Engineer | AWS Certified Cloud Practitioner
[GitHub](https://github.com/kofiampon72) · [Email](mailto:konadukofi88@gmail.com)

