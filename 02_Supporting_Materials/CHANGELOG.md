# Changelog

## [1.0.0] - Phase 0 freeze
### Frozen
- architecture specification frozen at architecture_spec_version 1.0.0
- Phase 0 implementation specification frozen with pilot_pack_version 1.0.0
- Data Unit schema frozen at data_unit_schema_version 1.0.0
- Evidence schema frozen at evidence_schema_version 1.0.0
- Agent API frozen at version 1.0.0

### Added
- versioning policy
- acceptance checklist
- known limitations list
- Phase 1 handoff package
- GOA minimum task chain definition
- MAN-02-01 and MAN-03-04 pilot folders, checklists, manifests, and sample material placeholder files
- MAN-02-01 and MAN-03-04 example request, data unit, and evidence files
- OpenClaw runtime bridge scripts and runtime bridge package
- OpenClaw runtime bridge, context bootstrap, package discoverability, textual workflow rendering, runtime rendering, and runnable validation records

### Validated
- OpenClaw workspace bridge documented and verified
- main-session context bootstrap verified
- runtime bridge package discoverability verified
- textual workflow rendering verified
- runtime rendering verified for Phase 0 in textual runtime form
- MAN-02-01 runnable dry-run verification completed successfully
- MAN-03-04 runnable dry-run verification completed successfully

### Notes
- the BELUCKS/OpenClaw project remains a multi-agent platform overall; Phase 0 completes only the single-agent minimum closed loop and boundary freeze
- evidence-schema freeze required a timeout recovery step:
  schemas/evidence/evidence-schema.json was first renamed to schemas/evidence/evidence-schema.json.bak-timeout, then rebuilt and frozen

## [0.1.0] - Phase 0 bootstrap
### Added
- repository skeleton
- architecture specification placeholder
- Phase 0 implementation specification placeholder
- Data Unit schema placeholder
- Evidence schema placeholder
- Agent API placeholder
- versioning policy
