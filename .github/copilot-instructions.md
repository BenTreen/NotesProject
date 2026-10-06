# Copilot Instructions — NotesProject

## Purpose
This repo is a hands-on learning project for an Azure infrastructure engineer to learn
Terraform and the full GitHub application development lifecycle, treating it as if it
were a real production application.

## Working style (read this first, every session)
- This is a **teaching exercise**. Do not run terminal commands, create/edit files or
  folders, or take any other action proactively — only when the user explicitly asks.
- Before any action, explain: what the command/file does, why it's needed, and what
  it's for. Let the user run commands / create files themselves.
- Wait for explicit confirmation that a step is complete before proposing the next one.
- **Whenever the user sets a new standing instruction or preference, explicit permission has been provided to update this file**
  to record it, so future sessions stay consistent without needing to be re-told.

## Project overview
- App: a simple Notes app (CRUD), chosen deliberately to be lightweight so the focus
  stays on the lifecycle/tooling rather than application complexity.
- Architecture: 3-tier — FastAPI backend API, Azure SQL Database, static frontend —
  hosted on Azure App Service.
- Repo: https://github.com/BenTreen/NotesProject

## Infrastructure & deployment rules
- All infrastructure is defined and managed via Terraform.
- All deployments (infra apply + app deploy) happen via GitHub Actions only — no local
  `terraform apply` or `az` deployment commands from a developer machine.
- Azure authentication uses OIDC federated credentials (no stored secrets/passwords).
- Each environment (dev/staging/prod) has its own Azure AD App Registration + federated
  credential scoped to the matching GitHub Environment name, and its own RBAC scope.
- One-time manual bootstrap steps (documented here, not repeated / not re-automated):
  - App Registration + federated credential per environment (created via Azure Portal)
  - Terraform remote state storage account (created via Azure Portal), container
    `tfstate`, one state file key per environment

## Environments
- `dev`, `staging`, `prod` — implemented as GitHub Environments with protection rules
  (prod requires manual approval before deploy).

## Conventions
*(to be filled in as decisions are made)*
- Branching strategy: TBD
- PR requirements: TBD
- Commit message style: TBD
