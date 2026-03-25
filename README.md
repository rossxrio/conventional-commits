# Conventional Commits — Quick Reference

A lightweight specification for writing structured, machine-readable commit messages.

## Syntax

```
type(scope)!: short description

[optional body]

[optional footer: BREAKING CHANGE: ...]
```

- **`type`** — what kind of change (required)
- **`scope`** — what area of the codebase (optional, in parentheses)
- **`!`** — signals a breaking change (optional)
- **description** — imperative mood, lowercase, no period. Write *add X*, not *adds X* or *Added X*

---

## Types

### `feat` — New feature
A new capability visible to users. Bumps the **minor** version in semver.

```
feat(auth): add OAuth2 login
feat(dashboard): show weekly summary chart
```

---

### `fix` — Bug fix
Corrects broken behaviour. Bumps the **patch** version.

```
fix(cart): correct item count on page reload
fix(api): handle null response from payment gateway
```

---

### `refactor` — Code restructure
Code reorganised with no new features and no bug fix. Observable behaviour stays the same.

```
refactor(api): extract auth logic into middleware
refactor(db): simplify query builder
```

---

### `docs` — Documentation only
READMEs, inline comments, wikis, changelogs — no code changes.

```
docs: add setup guide to README
docs(api): document rate limit headers
```

---

### `style` — Formatting only
Whitespace, semicolons, indentation — zero logic changes. Not CSS/UI styling.

```
style: run prettier across src/
style: fix inconsistent quote style
```

---

### `test` — Tests
Adding or fixing tests. No production code changed.

```
test(user): cover edge case for empty email field
test: add integration tests for checkout flow
```

---

### `chore` — Maintenance
Tasks that don't touch src or tests — dependency bumps, configs, tooling.

```
chore: bump eslint to v9
chore: update .gitignore for macOS artifacts
```

---

### `perf` — Performance improvement
A change that speeds things up without altering behaviour.

```
perf(db): add index on users.email
perf: lazy-load dashboard components
```

---

### `ci` — CI/CD pipeline
GitHub Actions, Dockerfiles, build scripts, deployment configs.

```
ci: cache node_modules in workflow
ci: add lint step to PR checks
```

---

### `feat!` / `BREAKING CHANGE` — Breaking change
Incompatible API change. Add `!` after the type, or include a `BREAKING CHANGE:` footer. Bumps the **major** version.

```
feat!: rename /users endpoint to /accounts

feat(api): drop XML response support

BREAKING CHANGE: XML responses are no longer returned.
Clients must use JSON.
```

> Breaking changes can pair with any type — `fix!` is valid if a bug fix breaks the API contract.

---

## Tips

| | |
|---|---|
| **Scope** | Use a module, layer, or package name: `feat(payments):`, `fix(ui):` |
| **Body** | Add after a blank line when context is needed — explain *what* and *why*, not *how* |
| **Footer** | For `BREAKING CHANGE:`, issue refs (`Closes #42`), or co-authors |
| **Subject length** | Keep under ~72 characters |
| **Multiple changes** | Split into separate commits — one type per commit |
