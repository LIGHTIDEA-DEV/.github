# Developer Repo Onboarding & Workflow Checklist

This guide is for **developers who join after repositories already exist** (imported or created).

It explains:

* How to access and clone repos
* How our branches work (`dev`, `main`, `feature/*`, `hotfix/*`)
* What you should be able to do (and what you should **not** be able to do)
* How to validate that your access and workflow are correct

---

## Where This Document Lives

**Location (recommended):**

```
.github/docs/DEVELOPER-ONBOARDING-WORKFLOW.md
```

Why:

* One place for all developers
* Always up to date
* Applies to every repo in the org

---

## 0) Before You Start (Account Requirements)

* [ ] You have joined the organization successfully
* [ ] **2FA is enabled** on your GitHub account
* [ ] You have access to the repository you need (ask Admins if not)

---

## 1) Clone the Repository

### Option A — HTTPS (simplest)

```bash
git clone https://github.com/<ORG>/<REPO>.git
cd <REPO>
```

### Option B — SSH (recommended if you already use SSH keys)

```bash
git clone git@github.com:<ORG>/<REPO>.git
cd <REPO>
```

**Expected result:** Repo downloads successfully. If you see permission denied, you do not have access or your auth is not configured.

---

## 2) Confirm Your Remotes and Current Branch

```bash
git remote -v
git status
git branch
```

**Expected result:**

* `origin` points to the GitHub org repository
* You are on `main` or `dev` locally

---

## 3) Fetch All Branches and Confirm `dev` Exists

```bash
git fetch --all --prune
git branch -a
```

Look for:

* `remotes/origin/dev`

If you do **not** see `dev`, contact Admins. Do not create random long-lived branches.

---

## 4) Update Your Local `dev`

```bash
git checkout dev 2>/dev/null || git checkout -b dev origin/dev
git pull origin dev
```

**Expected result:**

* Your local `dev` is up to date

---

## 5) Create a Feature Branch (Normal Work)

### Naming convention

* `feature/<ticket>-<short-description>`

Example:

```bash
git checkout dev
git pull origin dev
git checkout -b feature/1234-add-login-validation
```

---

## 6) Make Changes, Commit, and Push

```bash
git add .
git commit -m "<short meaningful message>"
git push -u origin feature/1234-add-login-validation
```

**Expected result:**

* Branch is created on GitHub
* You can now open a Pull Request

---

## 7) Open a Pull Request (PR)

### Default development flow

* PR from: `feature/*`
* PR to: `dev`

In GitHub:

* Open **Pull requests → New pull request**
* Base: `dev`
* Compare: your `feature/*`
* Fill the PR template

**Expected result:**

* Reviewers may be requested automatically
* You will receive comments or approval

---

## 8) Respond to Review Feedback

If changes are requested:

* Update your code locally
* Commit again
* Push again (same branch)

```bash
git add .
git commit -m "Address review comments"
git push
```

**Expected result:**

* The existing PR updates automatically

---

## 9) Promotion to `main` (Production)

Developers generally do **not** push to `main`.

Typical promotion is:

* `dev` → `main` via PR
* Reviewed/approved by **Admins Team** (CODEOWNERS)

---

## 10) What You Should NOT Do

### Do not push to `main`

This is blocked by policy.

**Test (optional, to confirm your permissions):**

```bash
git checkout main
git pull origin main
# create a harmless local file change
mkdir -p .tmp && echo test > .tmp/permission-test.txt
git add .tmp/permission-test.txt
git commit -m "test: verify main push is blocked"
git push origin main
```

**Expected result:**

* Push is rejected/blocked (permission denied / protected branch)

> After the test, clean up your local commit (recommended):

```bash
git reset --hard HEAD~1
rm -rf .tmp
```

### Do not bypass reviews

* Do not ask for shortcuts
* Do not merge without approvals

### Do not commit secrets

* Never commit passwords, tokens, private keys

---

## 11) Quick “Everything Works” Validation Checklist

After you join a repo, you should be able to confirm:

* [ ] You can clone the repo
* [ ] You can see `dev` branch (`origin/dev`)
* [ ] You can create and push `feature/*` branches
* [ ] You can open PRs into `dev`
* [ ] You **cannot** push directly to `main`
* [ ] PRs to `main` require Admin approvals (CODEOWNERS)

---

## 12) When to Contact Admins Team

Contact Admins if:

* You cannot see or clone a repo you should have access to
* `dev` branch is missing
* You receive permission errors pushing `feature/*`
* You are blocked by branch protections and think it’s incorrect

---

## Summary

* Work happens in `feature/*`
* Integration happens in `dev`
* Production-ready code is in `main`
* `main` is protected: PR + reviews required

Welcome — follow the process and you’ll never break production by accident.
