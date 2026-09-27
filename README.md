# autonomous-dev-environment

## Purpose

This repository serves as an autonomous software-development environment. It is designed so that AI agents, such as Jules, can operate securely and effectively by following strict instructions and governance rules before making any changes.

## Repository Structure

The repository is currently organized with governance and policy files at its root, as well as placeholder directories for future development:
- **`AGENTS.md`**: Core instructions and development rules for AI agents.
- **`CONTRIBUTING.md`**: Guidelines for branching, pull requests, and how to propose work.
- **`DEFINITION_OF_DONE.md`**: Quality, security, and functional requirements for a task to be considered complete.
- **`SECURITY.md`**: Security principles, rules around secrets, high-risk changes, and agent safety.
- **`docs/`**, **`scripts/`**, **`tests/`**, **`tickets/`**: Standard directories for documentation, tooling, testing, and task tracking.

*(Note: There is currently no application code or `package.json`. The existing CI setup is governance-only and verifies that the required policy files are present and no secrets are committed.)*

## Feature-Branch and Pull-Request Workflow

- **Branching**: The `main` branch is protected and kept production-ready. Every change must be made on a dedicated feature branch using descriptive prefixes (e.g., `feature/`, `fix/`, `docs/`, `audit/`). Direct commits to `main` are prohibited.
- **Pull Requests**: Every change must be proposed via a pull request. The PR description must follow the provided template, summarizing the change, explaining why it was required, listing the checks/tests run, noting any risks, and documenting follow-up items.
- **Checks**: Before requesting a review, all applicable lint, type-check, test, build, and security checks must be executed and pass.

## Expected Workflow and Responsibilities for AI Agents (Jules)

For every task, AI agents are expected to:
1. **Understand**: Read the entire assigned ticket and inspect relevant existing code.
2. **Isolate**: Work only within the assigned scope and use a dedicated feature branch.
3. **Implement**: Create the smallest complete solution without bypassing CI or disabling tests.
4. **Verify**: Add or update tests, run linting, type-checking, build commands, and relevant test suites.
5. **Review**: Check for security or regression risks, and update documentation as needed.
6. **Propose**: Open a pull request containing all required details.
7. **Escalate**: Stop and request a human review when requirements conflict, confidence is low, security-sensitive code is involved, or excessive repair attempts fail.

Agents must **never** commit secrets or `.env` files, weaken security controls, alter production infrastructure without approval, or merge their own changes.

## Required Checks Before Merge

According to the Definition of Done, a ticket is only complete when:
- **Functional**: Acceptance criteria are satisfied, behavior works as expected (including edge cases), and unrelated functionality remains unchanged.
- **Quality**: Linting, type checking, unit tests, relevant integration tests, and builds all pass. Existing tests must remain green.
- **Security**: No secrets are committed, inputs are validated, authorization rules are preserved, dependencies are reviewed, and no high-severity vulnerabilities are introduced.
- **Documentation**: Relevant documentation and configuration changes are updated.

## Security and High-Risk Change Rules

To maintain a secure environment, the following rules apply:
- **Secrets Management**: Passwords, API keys, private keys, and `.env` files must never be committed. They belong in GitHub Secrets or an approved secret manager.
- **High-Risk Changes**: Explicit human approval is required before merging changes involving authentication, authorization/RBAC, payments, production DB migrations, destructive data operations, infrastructure modifications, or critical dependency upgrades.
- **Agent Safety**: Agents must not expose secrets in logs, disable security tools, bypass branch protections, or execute unauthorized destructive commands. If a security issue is found, agents must stop, document the issue, and mark it for human review.

## Proposing Work (Future Contributors)

Human contributors and agents alike should follow these steps to propose new work:
1. Create a dedicated feature branch.
2. Make a scoped, complete change that satisfies all criteria in `DEFINITION_OF_DONE.md`.
3. Run all applicable checks locally (linting, tests, build).
4. Open a pull request against `main` using the repository's Pull Request template.
5. Wait for the repository owner to review and explicitly approve, particularly for high-risk changes.
