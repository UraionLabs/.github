# Security

If you believe you have found a security vulnerability in a Uraion Labs project, please report it privately. Do not open a public issue, pull request, or discussion.

## How to report

1. Use **GitHub Private Vulnerability Reporting** on the affected repository, if it is enabled: **Security → Report a vulnerability**.
2. If that option is not available, use the [Uraion Labs contact form](https://uraionlabs.com/#contact). Start the message with “Security” and include the repository name.

Include:

- The repository, package, or component
- A description of the issue and its impact
- Steps to reproduce, or a proof of concept
- Affected versions or commits, if known
- Any suggested fix, if you have one

Do not include credentials, production data, or other people’s personal information unless they are required to demonstrate the issue, and then only the minimum needed.

## Scope

This policy covers software, documentation, and infrastructure published by [Uraion Labs](https://github.com/UraionLabs).

Out of scope unless they create a vulnerability in our software:

- Bugs that require physical access, a compromised machine, or social engineering
- Reports from automated scanners with no demonstrated impact
- Third-party services and dependencies we do not control (report those to the upstream project)

## What to expect

We will acknowledge reports as soon as we can and keep the discussion private until a fix is released or we determine the report is not a vulnerability. We may ask for more detail. Please give us a reasonable window to patch before any public disclosure.

We do not currently operate a paid bug bounty.

## Preferred handling

If you have write access to a repository, do not push a fix for an unannounced vulnerability to a public branch. Coordinate through the private report so maintainers can prepare a release.
