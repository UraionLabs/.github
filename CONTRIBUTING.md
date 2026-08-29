# Contributing to Uraion Labs

These are organization-wide defaults for repositories under [Uraion Labs](https://github.com/UraionLabs). If a repository has its own `CONTRIBUTING.md`, follow that file.

## Before you start

- Read the repository README and any design or architecture docs it points to.
- Search existing issues and pull requests to avoid duplicates.
- Do not file a public issue for a security vulnerability. See [SECURITY.md](SECURITY.md).
- By participating, you agree to the [Code of Conduct](CODE_OF_CONDUCT.md).

Some repositories are private or not yet open for external contribution. If you cannot access a project, use the [website contact form](https://uraionlabs.com/#contact).

## Issues

Use the repository’s issue templates when they are available:

- **Bug report** — unexpected behavior, with steps to reproduce
- **Feature request** — a concrete problem and a proposed change

Include the repository, version or commit, environment, and enough detail for someone else to act on the report. Feature requests should explain the problem, not only the desired API.

## Pull requests

1. Fork the repository (or branch from the default branch if you have write access).
2. Create a focused branch.
3. Match the repository’s existing style, layout, and tooling. Do not reformat unrelated code.
4. Add or update tests when behavior changes.
5. Run the checks the repository documents (tests, linters, type checks, builds).
6. Open a pull request and fill in the template:
   - what changed
   - why
   - testing performed
   - breaking changes
   - related issues

Keep pull requests small enough to review. Separate refactors from behavior changes when you can.

Do not commit secrets, credentials, private keys, or personal data. Do not add generated artifacts unless the repository already requires them.

## Repository-specific rules

Language, build system, and review rules live in each repository. Typical places to look:

- `README.md`
- `CONTRIBUTING.md` in that repository
- CI configuration under `.github/workflows/`
- language tooling (`Cargo.toml`, `package.json`, `pyproject.toml`, and similar)

If this organization-wide guide and a repository guide disagree, the repository guide wins.

## Questions

- Project usage and defects: GitHub issues on the relevant repository. See [SUPPORT.md](SUPPORT.md).
- Product, research, or partnership inquiries: [uraionlabs.com/#contact](https://uraionlabs.com/#contact).
