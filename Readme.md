# Python CI with GitHub Actions

This project demonstrates how to automate Python testing using **GitHub Actions**.

## Workflow File

Location:

```
.github/workflows/unittest.yml
```

## Workflow Explanation

### 1. Workflow Name

```yaml
name: Python CI
```

This is the name displayed in the **Actions** tab.

---

### 2. Trigger

```yaml
on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main
```

The workflow runs whenever:
- Code is pushed to the `main` branch.
- A Pull Request is created for the `main` branch.

---

### 3. Create a Job

```yaml
jobs:
  test:
    runs-on: ubuntu-latest
```

Creates a job named **test** and runs it on an Ubuntu virtual machine.

---

### 4. Checkout Repository

```yaml
- name: Check out code
  uses: actions/checkout@v2
```

Downloads your GitHub repository into the runner.

---

### 5. Install Python

```yaml
- name: Set up Python
  uses: actions/setup-python@v4
  with:
    python-version: "3.11"
```

Installs Python 3.11.

---

### 6. Install Dependencies

```yaml
- name: Install dependencies
  run: |
    python -m pip install --upgrade pip
    if [ -f requirements.txt ]; then pip install -r requirements.txt; fi
```

- Upgrades `pip`
- Installs all packages listed in `requirements.txt`

---

### 7. Run Tests

```yaml
- name: Run tests
  run: |
    python -m unittest discover -s tests
```

Runs all unit tests inside the `tests` folder.

---

## Workflow Flow

```
Write Code
      ↓
git push
      ↓
GitHub Actions Triggered
      ↓
Checkout Repository
      ↓
Install Python
      ↓
Install Dependencies
      ↓
Run Tests
      ↓
Success / Failed
```

## Technologies Used

- Python
- Git
- GitHub
- GitHub Actions
- Unit Testing