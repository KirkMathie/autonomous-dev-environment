# Implementation Backlog

The repository uses `tickets/` as the executable backlog record. Ticket 001 is the previously completed Phase 1 architecture ticket. The implementation build is decomposed as follows; statuses remain `IN_PROGRESS` until required CI passes on the implementation PR.

| Epic | Ticket | Dependency | Status before CI |
| --- | --- | --- | --- |
| 1 Core domain and task state | `tickets/002-core-domain-state.md` | 001 | IN_PROGRESS |
| 2 Orchestrator | `tickets/003-orchestrator.md` | 002 | IN_PROGRESS |
| 3 Providers/workers | `tickets/004-provider-system.md` | 002 | IN_PROGRESS |
| 4 Routing/escalation | `tickets/005-routing-escalation.md` | 003,004 | IN_PROGRESS |
| 5 Safe tools | `tickets/006-safe-tools.md` | 002 | IN_PROGRESS |
| 6 Verification | `tickets/007-deterministic-verification.md` | 002 | IN_PROGRESS |
| 7 Evidence/observability | `tickets/008-evidence-audit.md` | 002,003 | IN_PROGRESS |
| 8 GitHub | `tickets/009-github-integration.md` | 002 | IN_PROGRESS |
| 9 CLI/demo | `tickets/010-cli-demo.md` | 003-009 | IN_PROGRESS |
| 10 Tests/docs/backlog | `tickets/011-tests-docs.md` | 002-010 | IN_PROGRESS |

A ticket is changed to `COMPLETE` only after implementation plus the required repository checks pass. The final CI verification commit records that transition.
