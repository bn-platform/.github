# BN Platform Engineering — GitHub Organization

This organization provides standardized project templates, reusable CI/CD workflows, and governance policies for all engineering teams.

## Organization Structure
```
bn-platform (org)
├── .github                  ← You are here. Org-level defaults and reusable workflows
├── template-dotnet          ← .NET project template (C# solution, xUnit, CI pipeline)
├── template-python          ← Python project template (src layout, pytest, Docker, CI pipeline)
└── template-terraform       ← Terraform/IaC template (modules, environments, CI pipeline)
```

## What the Platform Provides

**For every new repository created from a template:**

- Pre-configured CI pipeline (build, test, lint)
- PR template with change type, testing checklist, and work item linking
- Issue templates (bug report, feature request, infrastructure change)
- CODEOWNERS for platform review on workflow and infrastructure changes
- Branch protection via org-level ruleset (PRs required, no force push, no branch deletion)

**Reusable workflows** (in `.github/workflows/`):

| Workflow | Purpose | Status |
|----------|---------|--------|
| `dotnet-build.yml` | .NET restore → build → test | Stub — WS-2 |
| `docker-build-push.yml` | Docker build → Trivy scan → push to GHCR | Stub — WS-2 |
| `terraform-plan-apply.yml` | Terraform fmt → init → validate → plan | Stub — WS-2 |

## How to Use

1. Navigate to a template repo (e.g., `template-dotnet`)
2. Click **"Use this template"** → **"Create a new repository"**
3. Name your repo, select the org, and create
4. Clone and start working — CI pipeline, branch protection, and templates are inherited automatically

## Naming Conventions

| Type | Pattern | Example |
|------|---------|---------|
| Template repos | `template-{language/tool}` | `template-dotnet`, `template-python` |
| Demo consumer repos | `demo-{purpose}` | `demo-dotnet-api`, `demo-container-app` |
| Reusable workflows | `{tool}-{action}.yml` | `dotnet-build.yml`, `docker-build-push.yml` |

## Branch Protection

An org-level ruleset enforces the following on `main` across all repositories:

- All changes require a pull request (no direct pushes)
- No force pushes
- No branch deletion
- Stale reviews dismissed on new pushes

## Related

- [Azure DevOps IPC Platform](https://dev.azure.com) — Existing IPC pipeline infrastructure
- Workstream tracking: WS-1 (complete) → WS-2 (CI/CD workflows) → WS-3 (ADO parity)
