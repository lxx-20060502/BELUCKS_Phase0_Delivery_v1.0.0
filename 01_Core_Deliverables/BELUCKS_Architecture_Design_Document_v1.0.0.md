# BELUCKS Architecture Specification

- architecture_spec_version: 1.0.0
- status: frozen
- phase: Phase 0
- authoritative_framework: BEAM Plus Existing Buildings v3.0
- supported_frameworks_version: 1.0.0

## 1. Purpose
This document defines the canonical architecture, vocabulary, scope boundary, and agent boundary for the BELUCKS multi-agent building assessment platform during Phase 0.

## 2. Phase 0 Scope Freeze

### 2.1 In Scope
- BEAM Plus Existing Buildings v3.0 as the only authoritative framework
- Management (MAN) as the only priority category
- Pilot A: MAN-02-01 ESG Disclosure
- Pilot A: MAN-02-02 Net-zero Transition Plan
- Pilot A: MAN-02-03 Resilience Strategy
- Pilot B: MAN-03-04 Smart Facility Management
- Data Unit, Evidence, AgentRequest, AgentResult, and GOA Task as canonical platform objects
- OpenClaw single-agent workflow visibility
- Field-level alignment across architecture spec, Data Unit schema, and Agent API spec

### 2.2 Out of Scope
- LEED / GB / ESG external mapping execution
- Full certification scoring and rating
- B Agent / E Agent real execution in Phase 0
- Cross-Agent Arbitration Engine real execution
- Platform UI
- Full multi-agent orchestration in production form

## 3. Canonical Vocabulary

### 3.1 Framework Layer
- Framework
- Category
- Credit
- Clause

### 3.2 Assessment Layer
- Data Unit
- Evidence
- Rule Check
- Agent Result

### 3.3 Platform Layer
- GOA Task
- Conflict Group
- Mapping Target
- Project Result

## 4. Agent Boundary

### 4.1 GOA
GOA is the orchestration authority in Phase 1 planning and the architectural coordination point in Phase 0. GOA is responsible for:
- selecting target credits
- selecting target agents
- preparing data units
- passing evidence references
- collecting structured results
- generating unified logs

### 4.2 Single Agent Responsibility
A single agent is responsible only for evaluating bound data units and returning structured results. A single agent does not perform:
- total certification rating
- cross-agent conflict arbitration
- external framework mapping

### 4.3 Agent Priority
- Phase 0 implementation priority: GOA interface definition + L Agent executable path
- B Agent and E Agent: protocol reservation only
- Cross-Agent Arbitration Engine: interface reservation only
- Mapping Engine: interface reservation only

## 5. Fixed Single-Agent Workflow
The fixed single-agent workflow contains:
1. select_credit
2. load_clauses
3. generate_data_units
4. bind_evidence
5. validate_evidence
6. run_l_agent
7. summarize_result
8. emit_gap_report

## 6. Pilot Definition
Phase 0 pilots are divided into:
- Pilot A: rule-governance type credits
- Pilot B: operation-evidence type credits

Pilot A includes:
- MAN-02-01
- MAN-02-02
- MAN-02-03

Pilot B includes:
- MAN-03-04

## 7. Handoff Requirement
Phase 0 is considered complete only when:
- canonical vocabulary is frozen
- agent boundary is frozen
- Data Unit schema is frozen
- Evidence schema is frozen
- Agent API is frozen
- MAN-02-01 pilot is runnable
- MAN-03-04 pilot is runnable
- OpenClaw single-agent workflow is visible
- handoff package is prepared
