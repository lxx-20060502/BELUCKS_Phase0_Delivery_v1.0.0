# Versioning Policy

## 1. Controlled Specifications
The following specifications are version-controlled independently:
- architecture_spec_version
- data_unit_schema_version
- evidence_schema_version
- agent_api_version
- supported_frameworks_version
- pilot_pack_version

## 2. Change Levels
All changes must be classified into one of the following levels:

### patch
Used for:
- typo fixes
- wording clarification
- non-structural corrections
- examples that do not change the contract

### minor
Used for:
- additive fields
- additive endpoints
- backward-compatible extensions
- new reserved values
- new pilot content without breaking existing structure

### major
Used for:
- breaking field changes
- field removal or rename
- contract-breaking API changes
- changes to canonical vocabulary
- changes to agent boundary
- changes that invalidate existing pilot data or workflows

## 3. Synchronization Rule
If a change affects Data Unit, Evidence, AgentRequest, AgentResult, or GOA Task semantics, the following documents must be reviewed and updated together:
- docs/architecture/architecture-spec.md
- schemas/data-unit/data-unit-schema.json
- schemas/evidence/evidence-schema.json
- schemas/agent-api/agent-api-spec.yaml

## 4. Freeze Rule
After Phase 0 freeze, all modifications must be recorded in CHANGELOG.md before release.

## 5. Release Discipline
Every formal repository update should leave:
- an updated version field
- a changelog entry
- a commit message that states the change level
