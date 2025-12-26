# Developer 2FA Setup & Recovery Guide

This guide explains **what to do if you join the organization without Two-Factor Authentication (2FA)** enabled, or if you are blocked from access because 2FA is missing.

This applies to **all organization members**.

---

## Where This Document Lives

**Location (recommended):**

```
.github/docs/DEVELOPER-2FA-SETUP.md
```

Why:

* Central reference for security onboarding
* Reduces Admin support requests
* Aligns with GitHub’s mandatory 2FA policy

---

## Why 2FA Is Required

* GitHub requires 2FA for accounts that contribute code
* The organization enforces 2FA for all members
* Accounts without 2FA may be **blocked or removed automatically**

This is a **GitHub security requirement**, not optional.

---

## Scenario 1: You Have NOT Enabled 2FA Yet

### Step-by-step: Enable 2FA

1. Log in to **GitHub.com**
2. Go to:

```
Settings → Password and authentication
```

3. Under **Two-factor authentication**, click **Enable**

### Choose a 2FA method (recommended order)

1. ✅ **Authenticator App (TOTP)** (recommended)

   * DUO, Google Authenticator, Microsoft Authenticator, Authy
2. 🔐 **Passkey / Security key** (optional)
3. ⚠️ SMS (least secure, use only if needed)

---

## Scenario 2: You Joined the Org and Got Blocked or Removed

This happens when:

* You accepted an org invite without 2FA
* Or 2FA was disabled later

### What to do

1. Enable 2FA on your GitHub account (steps above)
2. Log out and log back in
3. Ask an **Admin** to re-send the organization invite (if needed)

Once 2FA is enabled, GitHub will allow access again.

---

## Scenario 3: You Lost Access to Your 2FA Device

### Option A — Use recovery codes

During 2FA setup, GitHub provides **recovery codes**.

1. Log in using a recovery code
2. Reconfigure your authenticator app

---

### Option B — Still locked out

If you:

* Lost your phone
* Did not save recovery codes

You must:

1. Contact **GitHub Support**
2. Complete account recovery

Admins cannot bypass GitHub account security.

---

## Recommended Setup (Best Practice)

* Use an **Authenticator App** (DUO recommended)
* Save recovery codes securely
* Optionally add a **passkey or hardware key**

---

## Verification Checklist

After setup, confirm:

* [ ] 2FA shows as **Enabled** in GitHub settings
* [ ] You can access organization repositories
* [ ] You can clone repositories
* [ ] You no longer see 2FA warning banners

---

## When to Contact Admins Team

Contact Admins if:

* You enabled 2FA but still cannot access repos
* You believe your org access is incorrect
* You need the invite re-sent

---

## Summary

* 2FA is mandatory
* Enable it **before** or **immediately after** joining
* Without 2FA, access will be blocked
* This protects both your account and the organization

Security is a shared responsibility.
