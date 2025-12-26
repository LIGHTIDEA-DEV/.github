# Golden Repository Baseline Checklist

This checklist defines the **mandatory baseline** for every repository imported into the organization.

Its purpose is to ensure **consistent security, governance, and workflow** across all projects.

Use this checklist **every time a new repository is imported**.

---

## Where This Document Lives

**Location (recommended):**

```
.github/docs/REPO-BASELINE-CHECKLIST.md
```

Why:

* Centralized and visible to all members
* Version-controlled
* Easy to reference during onboarding and audits

---

## 0. Repository Import & Visibility

* [ ] Repository is imported into the **organization** (not personal account)
* [ ] Repository visibility is set to **Private**
* [ ] Default branch is **`main`**

---

## 1. Access Control (Teams)

Go to: **Repo → Settings → Collaborators and teams**

* [ ] **Admins Team** added with **Admin** permission
* [ ] **Developers Team** added with **Write** permission
* [ ] No unnecessary individual users have direct access

---

## 2. Branch Setup

Go to: **Repo → Code**

* [ ] `dev` branch exists

  * [ ] Created from `main` if missing

---

## 3. `main` Branch Protection (Mandatory)

Go to: **Repo → Settings → Branches**

Confirm a branch protection rule exists for **`main`** with the following settings:

### Pull Request Enforcement

* [ ] Require pull request before merging
* [ ] Require at least **1 approval**
* [ ] Dismiss stale approvals when new commits are pushed
* [ ] Require conversation resolution before merging
* [ ] Require review from **Code Owners**

### Push Restrictions

* [ ] Restrict who can push to matching branches
* [ ] **Admins Team** is allowed
* [ ] **Developers Team is NOT allowed**

### Optional (Enable Later)

* [ ] Require approval of the most recent reviewable push
* [ ] Do not allow bypassing branch protection rules

---

## 4. CODEOWNERS File

Go to: **Repo → Code**

* [ ] File exists at:

  ```
  .github/CODEOWNERS
  ```
* [ ] Content includes:

  ```
  * @ORG-NAME/admins-team
  ```

  (Replace `ORG-NAME` with the actual organization name)

---

## 5. Pull Request Template

If using an **organization-wide PR template**, this step is already satisfied.

Otherwise, per repository:

* [ ] File exists at:

  ```
  .github/pull_request_template.md
  ```

---

## 6. Functional Validation (Must Pass)

Test with a **Developer** account:

* [ ] Developer can view and clone the repository
* [ ] Developer can push to `feature/*` branches
* [ ] Developer can push to `dev`
* [ ] Developer **cannot push directly to `main`**
* [ ] Developer can open PR → `main`
* [ ] PR automatically requests review from **Admins Team**
* [ ] PR cannot be merged without required approval

---

## 7. Final Confirmation

* [ ] Repository matches the organization’s **golden standard**
* [ ] Safe to onboard developers
* [ ] Safe to promote changes to `main`

---

## Notes

* This checklist should be reviewed periodically and updated as policies evolve
* Any deviation from this baseline must be explicitly approved by the Admins Team

---

**Status:** Approved baseline for all organization repositories
