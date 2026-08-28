# Repository Change Audit — 2026-08-28

## Targeted-change incident: PR #1

The intended change was limited to the test mock in `tests/unit/ui-utils.test.js`:

`configurable: true`

The merged PR #1 also changed `.github/workflows/ci.yml` and `package.json` to separate native Electron rebuilding from ordinary installation. GitHub's PR diff confirms three changed files.

Those two additional files were outside the stated targeted test scope and are therefore recorded as out-of-scope changes.

## Correction

The current `main` branch has been corrected so that:

- `tests/unit/ui-utils.test.js` retains `configurable: true`.
- `package.json` has been restored to the pre-PR #1 version.
- `.github/workflows/ci.yml` has been restored to the pre-PR #1 version.
- PR #2 remains closed and unmerged.
- No application runtime change from the targeted test fix is intentionally retained from PR #1.

## Evidence

PR #1: `ci: separate native rebuild from npm install`

PR #1 changed exactly three files:
- `.github/workflows/ci.yml`
- `package.json`
- `tests/unit/ui-utils.test.js`

The file-level diff establishes that the test mock change was accompanied by unrelated CI/package changes.

## Change-control rule

For a task explicitly limited to one test, no CI, dependency, package-script, application-runtime, documentation, refactor, deletion or relocation changes may be included unless separately authorised.

## Verification rule

Before future push/PR operations:
1. inspect `git diff --check`;
2. inspect `git diff --name-only`;
3. verify the changed-file list against the requested scope;
4. stop if any file is outside scope;
5. only then commit/push/create the PR.

## Historical integrity

The original merged PR is not erased. The corrective commits restore the two out-of-scope files while preserving the intended test change, so the full sequence remains visible in Git history.
