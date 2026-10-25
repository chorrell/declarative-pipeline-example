# Declarative pipeline example

[![CI](https://github.com/chorrell/declarative-pipeline-example/actions/workflows/main.yml/badge.svg)](https://github.com/chorrell/declarative-pipeline-example/actions/workflows/main.yml)
[![zizmor](https://github.com/chorrell/declarative-pipeline-example/actions/workflows/zizmor.yml/badge.svg)](https://github.com/chorrell/declarative-pipeline-example/actions/workflows/zizmor.yml)

A minimal [Jenkins declarative pipeline](https://www.jenkins.io/doc/book/pipeline/syntax/#declarative-pipeline)
example. There is no application code: the repository exists to show the
smallest useful `Jenkinsfile` and how to run it in CI without a Jenkins server.

## The pipeline

[`Jenkinsfile`](Jenkinsfile) defines a single `Build` stage that runs on any
agent and echoes a `VERSION` set in the `environment` block:

```groovy
pipeline {
  agent any

  environment {
    VERSION = '1.0.0'
  }

  stages {
    stage('Build') {
      steps {
        echo "Building ${VERSION}"
      }
    }
  }
}
```

## Running it

### In Jenkins

1. Create a **Pipeline** (or **Multibranch Pipeline**) job.
2. Set **Definition** to *Pipeline script from SCM* and point it at this
   repository.
3. Run the job. The console output shows `Building 1.0.0`.

### In GitHub Actions

The [CI workflow](.github/workflows/main.yml) runs the `Jenkinsfile` on every
push and pull request to `main` using
[Jenkinsfile Runner](https://github.com/jenkinsci/jenkinsfile-runner-github-actions),
which starts a throwaway Jenkins inside the job — no Jenkins server needed.

## CI

| Workflow | What it does |
| --- | --- |
| [`main.yml`](.github/workflows/main.yml) | Runs the `Jenkinsfile` with Jenkinsfile Runner |
| [`zizmor.yml`](.github/workflows/zizmor.yml) | Audits the GitHub Actions workflows with [zizmor](https://docs.zizmor.sh/) |

Actions are pinned to commit SHAs, and Dependabot proposes updates monthly.

## Contributing

Keep changes to the `Jenkinsfile` small and illustrative — this is a teaching
example, not a production pipeline. Branch from `main` and open a pull request;
CI runs both workflows.

## License

[Mozilla Public License 2.0](LICENSE)
