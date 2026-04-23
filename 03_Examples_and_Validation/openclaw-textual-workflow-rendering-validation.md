# OpenClaw Textual Workflow Rendering Validation

- phase: Phase 0
- status: draft

## 1. Purpose
This document records the validation result that a fresh OpenClaw main session can read the materialized workflow package and render the workflow into an ordered textual step list.

## 2. Validation Target
The validated package path is:

~/.openclaw/workspace/runtime-materialized/single-agent-workflow

The two key files used in validation are:
- single-agent-workflow.config.json
- single-agent-workflow.md

## 3. Validation Method
A brand-new OpenClaw main session was opened in the control UI.
The following prompt was sent:

请读取 ~/.openclaw/workspace/runtime-materialized/single-agent-workflow 里的 single-agent-workflow.config.json 和 single-agent-workflow.md，把这个 workflow 渲染成按顺序展开的步骤清单，并告诉我一共有几步。

## 4. Observed Result
The new session successfully returned an ordered workflow step list and correctly reported a total of 8 steps.

The returned steps included:
1. select_credit
2. load_clauses
3. generate_data_units
4. bind_evidence
5. validate_evidence
6. run_l_agent
7. summarize_result
8. emit_gap_report

## 5. Conclusion
Textual workflow rendering is verified for the materialized runtime package.

This validation confirms:
- the materialized runtime package is readable from a fresh OpenClaw main session
- OpenClaw can convert the workflow files into an ordered textual execution checklist
- the workflow step count can be recovered correctly as 8

## 6. Not Yet Verified
This validation does not prove:
- graphical workflow rendering in a dedicated UI component
- executable workflow run completion
- MAN-02-01 runnable verification
- MAN-03-04 runnable verification
