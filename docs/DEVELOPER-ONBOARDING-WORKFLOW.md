# Developer Repo Onboarding & Workflow Checklist

This guide is for **developers who join after repositories already exist** (imported or created).

It explains:

* How to authenticate and clone repositories
* How our branches work (`dev`, `main`, `feature/*`, `hotfix/*`)
* What you should be able to do (and what you should **not** be able to do)
* How to validate that your access and workflow are correct

---

## Where This Document Lives

**Location (recommended):**

`.github/docs/DEVELOPER-ONBOARDING-WORKFLOW.md`

Why:

* One place for all developers
* Always up to date
* Applies to every repo in the organization

---

## 0) Before You Start (Account Requirements)

Before cloning any repository, confirm:

* You have joined the organization successfully
* **2FA is enabled** on your GitHub account
* You have access to the repository you need (ask Admins if not)

---

## 1) Authenticate to GitHub (Before Cloning)

All repositories in this organization are **private**.
You must authenticate with GitHub **before** cloning any repository.

We standardize on **HTTPS authentication**.
SSH is optional and only for developers who already use it.

---

### Windows (Recommended)

Windows developers should use **Git Credential Manager (GCM)**, which is included with Git for Windows.

Steps:

1. Install Git for Windows (if not already installed): [https://git-scm.com/download/win](https://git-scm.com/download/win)
2. Open **Git Bash** or **PowerShell**
3. When cloning (next section), a browser window will open
4. Log in to GitHub and approve access

Expected result:

* Browser login happens once
* Credentials are stored securely
* Future `git pull` / `git push` works automatically

---

### Linux (Recommended)

Linux developers should also use **HTTPS authentication**.

**Preferred: Browser / device login**

When running the clone command, GitHub may prompt for a browser or device login.
Follow the instructions and approve access.

**Fallback (Only if browser login does not work): Personal Access Token (PAT)**

If your environment blocks browser/device login:

1. Create a **Fine-grained Personal Access Token**

   * Resource owner: the organization
   * Repository access: only required repositories
   * Permission: **Contents → Read and write**
2. Use the token when cloning (token replaces your password)

PATs are personal and must never be shared.

---

### SSH (Optional / Advanced Users Only)

Only use SSH if you already have SSH keys configured with GitHub.

`git clone git@github.com:<ORG>/<REPO>.git`

If SSH fails, use HTTPS instead.

---

## 2) Clone the Repository

Once authenticated, clone the repository:

`git clone https://github.com/<ORG>/<REPO>.git`

`cd <REPO>`

Expected result:

* Repository downloads successfully
* No authentication or permission errors

If you see **Repository not found**, authentication is missing or incorrect.

---

## 3) Verify the Repository Is Set Up Correctly

After cloning, run:

`git remote -v`

`git branch -a`

You should see:

* `origin` pointing to the organization repository
* `origin/main`
* `origin/dev`

If `dev` is missing or you cannot see the repo, contact **Admins Team**.

---

## 4) Update Your Local `dev`

`git checkout dev 2>/dev/null || git checkout -b dev origin/dev`

`git pull origin dev`

Expected result:

* Your local `dev` branch is up to date

---

## 5) Create a Feature Branch (Normal Work)

Naming convention:

* `feature/<ticket>-<short-description>`

Example:

`git checkout dev`

`git pull origin dev`

`git checkout -b feature/1234-add-login-validation`

---

## 6) Make Changes, Commit, and Push

`git add .`

`git commit -m "<short meaningful message>"`

`git push -u origin feature/1234-add-login-validation`

Expected result:

* Branch is created on GitHub
* You can now open a Pull Request

---

## 7) Open a Pull Request (PR)

Default development flow:

* PR from: `feature/*`
* PR to: `dev`

In GitHub:

* Open **Pull requests → New pull request**
* Base: `dev`
* Compare: your `feature/*`
* Fill the PR template

Expected result:

* Reviewers may be requested automatically
* You will receive comments or approval

---

## 8) Respond to Review Feedback

If changes are requested:

* Update your code locally
* Commit again
* Push again (same branch)

`git add .`

`git commit -m "Address review comments"`

`git push`

Expected result:

* The existing PR updates automatically

---

## 9) Promotion to `main` (Production)

Developers generally do **not** push to `main`.

Typical promotion flow:

* `dev` → `main` via Pull Request
* Reviewed and approved by **Admins Team** (CODEOWNERS)

---

## 10) What You Should NOT Do

### Do not push to `main`

This is blocked by policy.

Optional test (to confirm your permissions):

`git checkout main`

`git pull origin main`

`mkdir -p .tmp && echo test > .tmp/permission-test.txt`

`git add .tmp/permission-test.txt`

`git commit -m "test: verify main push is blocked"`

`git push origin main`

Expected result:

* Push is rejected (protected branch)

Cleanup after test:

`git reset --hard HEAD~1`

`rm -rf .tmp`

---

### Do not bypass reviews

* Do not ask for shortcuts
* Do not merge without approvals

### Do not commit secrets

* Never commit passwords, tokens, private keys

---

## 11) Quick “Everything Works” Validation Checklist

After joining a repo, you should be able to confirm:

* You can authenticate successfully
* You can clone the repo
* You can see `origin/dev`
* You can create and push `feature/*` branches
* You can open PRs into `dev`
* You **cannot** push directly to `main`
* PRs to `main` require Admin approvals

---

## 12) When to Contact Admins Team

Contact Admins if:

* You cannot see or clone a repo you should have access to
* `dev` branch is missing
* You receive permission errors pushing `feature/*`
* You are blocked by branch protections and believe it is incorrect

---

## Summary

* Work happens in `feature/*`
* Integration happens in `dev`
* Production-ready code lives in `main`
* `main` is protected: Pull Requests + reviews required

Welcome — follow the process and you’ll never break production by accident.
