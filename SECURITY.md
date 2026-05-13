# Security Policy

## Supported Versions

| Version | Supported |
|---------|-----------|
| `main`  | ✅ Yes     |

Only the current `main` branch receives fixes.

## Reporting a Vulnerability

Do not open a public issue for security-sensitive documentation problems.

Report concerns privately by emailing **coding.projects.1642@proton.me**.

Include:
- the affected page or section
- the risky or sensitive content
- the expected public-safe wording

## Scope

The main security concern for this site is accidental publication of private
topology, private paths, private endpoints, or other sensitive operational
details.

## Hardening Guidance

- Treat the docs as public-safe output only
- Keep private graph data in the private manifest repositories
- Use RepoGraph/manifest vocabulary consistently with the architecture charter
