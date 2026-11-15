# ProofOfWork — Two-Developer Collaboration Guide

Welcome to the **ProofOfWork** engineering team! This guide explains how both developers (**Huzaifa** and **Friend**) collaborate seamlessly using Git and GitHub without code collisions or merge headaches.

---

## 🌳 The Core Branch Strategy

We maintain two permanent branches in this repository:

1. **`main` (Production Branch):**
   - **Purpose:** Contains only production-ready, thoroughly tested, and verified code.
   - **Rule:** **NEVER** commit or push directly to `main`. Code only enters `main` via an approved Pull Request from `develop` when a milestone is completed.

2. **`develop` (Integration Branch):**
   - **Purpose:** The primary development hub where all completed features meet and integrate.
   - **Rule:** Both developers create their feature branches from `develop` and merge back into `develop`.

---

## 🏷️ Feature Branch Naming Rules

Whenever you begin a new task, create a dedicated branch off `develop`. Do not create long-lived personal branches. Each task gets its own branch.

### Feature Branches:
- `feat/huzaifa/task-name` (e.g., `feat/huzaifa/candidate-dashboard`)
- `feat/friend-name/task-name` (e.g., `feat/ali/company-dashboard`)

### Bug-fix Branches:
- `fix/huzaifa/bug-name` (e.g., `fix/huzaifa/login-validation-error`)
- `fix/friend-name/bug-name` (e.g., `fix/ali/prisma-query-timeout`)

---

## 🔄 Daily 8-Step Collaboration Workflow

Follow these 8 steps every time you work on a feature:

```
[develop] ➡️ create branch ➡️ [feat/.../...] ➡️ write code & test
   ⬆️                                              ⬇️
merge PR ⬅️ review & approve ⬅️ create PR ⬅️ push branch to GitHub
```

### Step 1: Clone the Repository (First time only)
```bash
git clone https://github.com/Huzaifa12-jutt/ProofOfWork.git
cd ProofOfWork
```

### Step 2: Switch to `develop` and Pull the Latest Changes
Always ensure your local `develop` branch has the latest updates before starting a task:
```bash
git checkout develop
git pull origin develop
```

### Step 3: Create Your Feature Branch
```bash
# Example for Huzaifa:
git checkout -b feat/huzaifa/candidate-dashboard

# Example for Friend:
git checkout -b feat/friend-name/auth-api
```

### Step 4: Write Code, Test Locally, and Commit
Keep your commits small, focused, and descriptive. Follow conventional commit messages:
- `feat: add candidate profile form schema`
- `fix: resolve JWT expiration handling`
- `docs: update API contract for assessments`
- `test: add unit tests for password hashing`

```bash
git add .
git commit -m "feat: descriptive message here"
```

### Step 5: Push Your Branch to GitHub
```bash
git push -u origin feat/your-name/your-task
```

### Step 6: Open a Pull Request (PR) on GitHub
1. Go to the repository on GitHub: `https://github.com/Huzaifa12-jutt/ProofOfWork`
2. Click **Compare & pull request**.
3. **IMPORTANT:** Set the **base branch** to `develop` (NOT `main`).
4. Describe:
   - What you built.
   - How you tested it.
   - Any database or API changes.

### Step 7: Code Review & Testing
- The other developer reviews the pull request.
- Check the code diff: Ensure no secret keys, debug console logs, or broken logic were added.
- Pull the branch locally to verify tests pass if needed.
- Click **Approve** and **Merge** (Squash and merge or Rebase and merge).

### Step 8: Clean Up Local Branch
Once merged, delete your feature branch locally and on GitHub to keep things clean:
```bash
git checkout develop
git pull origin develop
git branch -d feat/your-name/your-task
```

---

## 🔒 Moving Tested Releases to `main`

Once a complete milestone (e.g., Week 2 Foundation, Week 4 Auth) is integrated and thoroughly tested in `develop`:
1. Open a PR from `develop` into `main`.
2. Both developers review and confirm end-to-end functionality.
3. Merge the PR into `main`.
4. Tag the release (e.g., `git tag v1.0.0-m1`).

---

## ⚠️ Important Safety Rules

1. **Never use force push (`git push -f`)** on shared branches (`main` or `develop`).
2. **Never commit `.env` or sensitive credentials.** Always verify `.gitignore` is active.
3. **Never push directly to `main`.** All changes must pass review via Pull Request.
4. If a merge conflict occurs, pull `develop` into your feature branch, resolve the conflict locally, test, and then push.
