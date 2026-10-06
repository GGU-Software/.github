# GGU-Software Organization Workflows

This repository no longer contains workflow templates.

The shared GitHub Actions pipelines of the organization live in
[ggu-build-management](https://github.com/GGU-Software/ggu-build-management) under
`.github/workflows/` and are called as reusable workflows, not copied:

| Workflow | Purpose |
|----------|---------|
| `delphi-ci.yml` | Push CI: triggers the Jenkins `CI` job for repositories listed in `buildconfig.json` |
| `trigger-jenkins.yml` | Triggers any parameterized Jenkins job and optionally waits for it |
| `preview-ggu.yml` | Preview build of a ticket branch |
| `publish-ggu.yml` | Release build and publishing |
| `secure-and-package.yml` | Signing, encryption and packaging of a prebuilt executable |

Example caller:

```yaml
jobs:
  ci:
    uses: GGU-Software/ggu-build-management/.github/workflows/delphi-ci.yml@main
```

Jenkins credentials are provided by the self-hosted runner. Repositories need no Jenkins
secrets. Setup and rollout: `pipelines/CI build/README.md` in ggu-build-management.
