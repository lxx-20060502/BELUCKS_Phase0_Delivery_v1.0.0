# Phase 0 Implementation Specification

- phase: Phase 0
- status: frozen
- pilot_pack_version: 1.0.0

## 1. Objective
Phase 0 is used to freeze the minimum implementable structure required for the BELUCKS platform, so that later phases can proceed on a stable, version-controlled, and auditable foundation.

## 2. Authoritative Basis
- authoritative_framework: BEAM Plus Existing Buildings v3.0
- priority_category: Management (MAN)

## 3. Pilot Credits
The pilot credits in Phase 0 are:
- MAN-02-01 ESG Disclosure
- MAN-02-02 Net-zero Transition Plan
- MAN-02-03 Resilience Strategy
- MAN-03-04 Smart Facility Management

## 4. Canonical Objects to Freeze
The following objects must be frozen in Phase 0:
- Framework
- Category
- Credit
- Clause
- Data Unit
- Evidence
- AgentRequest
- AgentResult
- GOA Task

## 5. Phase 0 Agent Boundary
Phase 0 only establishes:
- GOA interface boundary
- L Agent executable path
- B Agent protocol reservation
- E Agent protocol reservation
- Cross-Agent Arbitration interface reservation
- Mapping Engine interface reservation

## 6. Fixed Single-Agent Workflow
The fixed workflow for the Phase 0 executable path is:
1. select_credit
2. load_clauses
3. generate_data_units
4. bind_evidence
5. validate_evidence
6. run_l_agent
7. summarize_result
8. emit_gap_report

## 7. Minimum OpenAPI Set
The minimum API set for Phase 0 contains:
- POST /credits/load
- POST /data-units/generate
- POST /evidence/bind
- POST /agents/run
- POST /goa/tasks/create
- GET /goa/tasks/{task_id}

## 8. Minimum Acceptance Requirement
Phase 0 is accepted only when:
- architecture vocabulary is frozen
- Data Unit schema is frozen
- Evidence schema is frozen
- Agent API is frozen
- MAN-02-01 pilot is runnable
- MAN-03-04 pilot is runnable
- OpenClaw single-agent workflow is visible
- versioning policy is established
- Phase 1 handoff package is prepared
