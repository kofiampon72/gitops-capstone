# Getting Started — New Contributor Guide
> You should be able to make your first commit in under 1 hour.

## 1. Environment Setup (10 minutes)
- Install Python 3.10+: https://www.python.org/downloads/
- Install Git: https://git-scm.com/
- Configure Git:
  ```bash
  git config --global user.name "Your Name"
  git config --global user.email "your@email.com"
  ```

## 2. Clone and Install (5 minutes)
```bash
git clone https://github.com/YOUR_USERNAME/gitops-cicd-capstone.git
cd gitops-cicd-capstone
pip install -r requirements.txt
```

## 3. Running Tests (2 minutes)
```bash
pytest test_app.py -v
```
All 8 tests should show PASSED. If any fail, do not proceed —
check your Python version and dependencies first.

## 4. Running the Linter (1 minute)
```bash
flake8 app.py test_app.py
```
No output = no lint errors. This must pass before you can open a PR.

## 5. Branch Workflow (5 minutes)
```bash
# Pick a task from Trello Backlog first!
git checkout main
git pull origin main
git checkout -b feature/TRELLO-###-short-description
# Do your work
git add .
git commit -m "[TRELLO-###] Your descriptive message"
git push origin feature/TRELLO-###-short-description
```

## 6. Opening a Pull Request (5 minutes)
1. Go to the GitHub repository
2. Click "Compare & pull request"
3. Title: `[TRELLO-###] Brief description`
4. Fill in the description
5. Click "Create pull request"
6. Request a reviewer from the right panel

## 7. After CI Passes
- Wait for all green checkmarks
- If anything is red, read the logs and fix it
- Once green, a team member merges the PR

## Troubleshooting
| Problem | Solution |
|---------|----------|
| `ModuleNotFoundError: flask` | Run `pip install -r requirements.txt` |
| Flake8 reports `E501 line too long` | Keep lines under 88 characters |
| Pytest shows `FAILED` | Read the error message — check the assert values |
| Push rejected | Make sure you are NOT on `main`. Use a feature branch. |

