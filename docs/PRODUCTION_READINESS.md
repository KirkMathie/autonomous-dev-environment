# Production-Readiness Checklist

The local control-plane vertical slice is implemented and tested. Production enablement still requires operator-owned deployment controls.

## Implemented

- [x] Typed domain schemas and explicit validated state machine.
- [x] Durable resumable state, append-only events/evidence, redaction, and idempotency.
- [x] Common provider contract with OpenAI, Jules, Jev, and mocks.
- [x] Deterministic risk routing and human approval gates.
- [x] Least-privilege tool registry/policy/executor.
- [x] Deterministic repository/lint/type/unit/integration/build/security/scope/secret/diff verification.
- [x] Completion invariant preventing green state after failed required checks.
- [x] GitHub adapter with no merge capability.
- [x] CLI create/run/resume/status/approve/reject/cancel/evidence/summary/demo.
- [x] Unit, integration, contract, and security tests.
- [x] Credential-free demo including failed-check repair path.

## Required before production credentials are enabled

- [ ] Run the orchestrator inside a hardened container/VM profile with OS-level filesystem/network restrictions.
- [ ] Store all keys in an approved secret manager and use least-privilege, short-lived GitHub credentials where possible.
- [ ] Validate the exact OpenAI model selection and rate/cost limits for the production account.
- [ ] Validate the current Jules source/session configuration and establish a controlled patch-reconciliation workflow.
- [ ] Validate the pinned TypeSafe API base URL/model and production quota/latency behavior.
- [ ] Define retention/rotation for `.ade` evidence and any sensitive repository metadata.
- [ ] Add organization-specific allowed command/path policies and dependency approval workflow.
- [ ] Load/chaos test concurrent runs if multi-process execution is planned. The current file store is designed for durable single-orchestrator use, not distributed locking.
- [ ] Complete threat modeling for prompt injection and remote provider compromise in the intended deployment network.

No live credentials are committed by this repository.
