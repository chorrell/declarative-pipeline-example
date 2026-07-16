# AGENTS.md

A minimal Jenkins declarative pipeline example.

## Project Layout

```text
.
├── Jenkinsfile   # Single-stage declarative pipeline (Build stage)
├── README.md
├── LICENSE
└── .github/workflows/
    └── main.yml
```

## Usage

This repo has no application code to build — it exists to demonstrate a
Jenkins declarative pipeline. To try it:

1. Point a Jenkins pipeline job at this repo.
2. Jenkins reads `Jenkinsfile` and runs the `Build` stage, which echoes the
   pinned `VERSION` environment variable.

## Code Style

- Keep `Jenkinsfile` minimal and declarative (`pipeline { agent any ... }`).
- Increment `VERSION` in the `environment` block when demonstrating changes.

## CI/CD

- `.github/workflows/main.yml`: GitHub Actions workflow (see file for current
  checks; this repo's CI badge in README points to it).

## Contributing

1. Branch from `main`.
2. Keep changes to `Jenkinsfile` small and illustrative — this is a teaching
   example, not a production pipeline.
3. Open a PR; CI runs the configured GitHub Actions workflow.
