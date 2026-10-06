# Progress Log — NotesProject

## Purpose
Tracks what's actually been done in this project so a new chat session (or a dropped
session) can pick up where things left off without re-deriving state. Update this file
as steps are completed — standing permission has been given to keep it current.

## Completed
- Configured local `git` username/email
- `git init` in project root
- Created `.gitignore` (Terraform, Python, editor/OS entries)
- First commit (`.gitignore`) and pushed to GitHub
- Repo created on GitHub: https://github.com/BenTreen/NotesProject (made **public** to
  unlock environment protection features on the Free plan)
- Renamed default branch `master` -> `main` (locally and on GitHub)
- Created GitHub Environments: `dev`, `staging`, `prod`
- `prod` environment: Deployment branches restricted to `main` only
  (Required reviewers was attempted but is not usable for a solo-owner repo with no
  other collaborators — the reviewer picker has nobody to select. Using a PR-gate on
  `main` instead as the practical equivalent.)
- Branch protection ruleset on `main`: requires a pull request before merging
  (0 required approvals, since solo maintainer for now)
- Enabled `fetch.prune` globally (auto-cleans stale local refs to deleted remote branches)
- Created repo folder structure: `terraform/`, `backend/`, `frontend/`,
  `.github/workflows/` (each with a placeholder `.gitkeep`)

## Decided conventions
- Default branch: `main`
- Environment names: `dev`, `staging`, `prod` (industry-standard 3-stage, chosen over
  `dev`/`test`/`prod`)
- Prod approval gate: enforced via PR-required branch protection on `main` +
  deployment-branch restriction on `prod`, not GitHub's Required Reviewers (unavailable
  for solo personal repos with no collaborators)

## Not yet done / next steps
- Write Terraform for infrastructure (App Service, Azure SQL)
- Set up Azure AD App Registrations + federated credentials per environment (manual,
  one-time bootstrap — see copilot-instructions.md)
- Set up Terraform remote state storage account (manual, one-time bootstrap)
- Scaffold FastAPI backend and static frontend
- Write GitHub Actions workflows (CI, Terraform plan/apply, app deploy) scoped per
  environment
