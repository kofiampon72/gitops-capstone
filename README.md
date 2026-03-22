# Capstone Project 1 — GitOps Workflow & CI Automation

## Project Overview
<Brief description: what this repo does, what problem it solves,
what technologies are used — 2-3 paragraphs>

## Architecture
```
Trello Board → Developer Machine → GitHub → GitHub Actions → Trello Board
     │                                            │
     │ Task Tracking                   Lint + Test + Trello Automation
     │                                            │
     └────────────────── Single Source of Truth ──┘
```
<Explain each component's role in 1-2 sentences>

## Workflow Description
1. Developer picks a task from Trello Backlog
2. Creates a feature branch: `feature/TRELLO-###-description`
3. Writes code, commits with `[TRELLO-###] message` format
4. Opens a Pull Request → CI triggers → Card moves to In Progress
5. Requests review → Card moves to Review/QA
6. CI must pass (lint + tests) before merge is allowed
7. PR merged → Card moves to Done automatically

## Commit Convention
Every commit must reference a Trello card ID:
```
[TRELLO-###] Short description

Optional longer explanation of what and why (not how).
```
Example: `[TRELLO-002] Add GitHub Actions CI pipeline with lint and test`

## Setup Instructions
### Prerequisites
- Python 3.10+
- pip
- Git

### Install
```bash
git clone https://github.com/YOUR_USERNAME/gitops-cicd-capstone.git
cd gitops-cicd-capstone
pip install -r requirements.txt
```

### Run Tests Locally
```bash
pytest test_app.py -v
```

### Run Lint Locally
```bash
flake8 app.py test_app.py
```

## Reflection

### 1. What is GitOps and why does it matter?
<200-300 words — Explain the principle that Git is the single
source of truth. Discuss how this project demonstrates GitOps
through Trello-linked commits, branch strategies, and automated
pipeline enforcement. Include real-world parallels.>

### 2. What problems does CI/CD solve in a team?
<200-300 words — Discuss "works on my machine" problems,
broken code in main, inconsistent standards. Explain how automated
lint and test gates address these. Reference specific stages in your ci.yml.>

### 3. What is the value of a branching strategy?
<200-300 words — Explain why main should always be deployable,
how feature branches isolate work, and what happens without them.
Reference the feature/TRELLO-### convention and PR review gates.>

### 4. What did you learn from the failed build?
<200-300 words — Describe what you did to trigger the failure,
what the CI output showed, how you fixed it, and what this
demonstrated about automated quality gates.>

### 5. How does this workflow support onboarding new developers?
<200-300 words — Explain how GETTING_STARTED.md enables a new
developer to be productive in under 1 hour. Discuss the role
of documentation, consistent conventions, and automated checks
in reducing onboarding friction.>
