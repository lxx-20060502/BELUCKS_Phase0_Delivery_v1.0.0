# BELUCKS_Phase0_Delivery_v1.0.0
BELUCKS Phase 0 核心交付物對照說明（中文）

本倉庫包含 BELUCKS / OpenClaw 專案的正式 Phase 0 交付包。
Phase 0 的目的，是統一系統語言、凍結關鍵抽象、明確 BELUCKS Agent 的職責邊界、定義 Data Unit 模型、定義 Agent 輸入 / 輸出協議，並確定首批支援的框架與認證範圍。Phase 0 架構文件已明確標示為 Phase 0、frozen、版本 1.0.0，並說明其用途是定義 BELUCKS 多代理建築評估平台在 Phase 0 的 canonical architecture、vocabulary、scope boundary 與 agent boundary。

1. 文件夾與文件對應關係

Phase 0 要求的三個核心交付物放在：

01_Core_Deliverables/

對應文件如下：

1.1 《BELUCKS 架構設計文檔》

文件夾： 01_Core_Deliverables/
文件： BELUCKS_Architecture_Design_Document_v1.0.0.md

1.2 《Data Unit Schema》

文件夾： 01_Core_Deliverables/
文件： BELUCKS_Data_Unit_Schema_v1.0.0.json

1.3 《Agent API 規範》

文件夾： 01_Core_Deliverables/
文件： BELUCKS_Agent_API_Spec_v1.0.0.yaml

2. 三個交付物分別如何完成 Phase 0 要求
2.1 《BELUCKS 架構設計文檔》

這份文件完成與 統一系統語言、凍結關鍵抽象、明確 Agent 職責邊界、以及 確定首批支援框架與認證範圍 有關的要求。

它的作用主要體現在以下幾點：

它定義了平台的 canonical vocabulary，並分成三層：
Framework Layer（Framework、Category、Credit、Clause）、
Assessment Layer（Data Unit、Evidence、Rule Check、Agent Result）、
Platform Layer（GOA Task、Conflict Group、Mapping Target、Project Result）。
這正是 Phase 0「統一系統語言」的直接落地。
它清楚定義了 Phase 0 的 in scope 與 out of scope。
例如，外部映射執行、完整認證評分、B Agent / E Agent 真實執行、真實跨 Agent 裁決、平台 UI，以及完整生產形態的多 Agent 協作，都被明確排除在 Phase 0 之外。
因此這份文件確實做到了「關鍵抽象凍結」，而不只是高層概念描述。
它明確定義了 BELUCKS 的 Agent 邊界。
文檔指出，GOA 負責 selecting target credits、selecting target agents、preparing data units、passing evidence references、collecting structured results、generating unified logs。
同時，single agent 只負責 evaluating bound data units 並返回 structured results，不負責總評級、跨 Agent 衝突裁決、外部框架映射。
這直接完成了 Phase 0 對 Agent 職責邊界的要求。
它明確確定了首批支援的框架與認證範圍。
架構文件指定 BEAM Plus Existing Buildings v3.0 為唯一 authoritative framework，指定 Management (MAN) 為唯一 priority category，並選定以下 pilot credits：
MAN-02-01、MAN-02-02、MAN-02-03、MAN-03-04。
這完成了「確定首批支援的法規與認證體系」這一要求。
2.2 《Data Unit Schema》

這份文件完成的是 定義 Data Unit（原子評估單元）模型 的要求，同時也在資料模型層面支撐了 Phase 0 的抽象凍結。

它的作用主要體現在以下幾點：

它明確標示為 data_unit_schema_version: 1.0.0，並且狀態為 frozen，因此它是一份正式凍結的 schema 文件，而不是非正式草稿。
它定義了 Data Unit 的 identification 結構，包括：
data_unit_id、framework_id、framework_version、credit_code、clause_id、unit_name、unit_type。
這些字段使每個 Data Unit 都能對應到具體 framework、credit 與 clause。
它定義了 Data Unit 的規則結構，包括：
atomic_claim、decision_method、required_evidence_types、endorsement_required、public_disclosure_acceptable、time_window_rule、buffer_rule。
這些字段使 Data Unit 成為真正可判定的原子評估單元，而不是只有名稱的記錄。它們說明了「要判什麼、怎麼判、需要什麼證據」。
它定義了 tags 與 multimodal references，包括 discipline、jurisdiction、time_scope、confidence，以及 document、BIM、tabular、API、manual input、geometry、timeseries 等來源引用。
這讓 Data Unit 在 Phase 0 就具備面向後續執行的擴展性。
它還為後續階段保留了 conflict 與 external mapping 的欄位，例如衝突裁決相關字段與 external mapping reservation。
這使得 Phase 0 的 schema 能與後面的跨 Agent 裁決與對外評分映射保持兼容，同時又不會把後續階段的執行內容提前塞進 Phase 0。

補充說明：
在目前這個 Phase 0 交付包中，Data Unit 交付物的正式形態是 JSON schema。
也就是說，原始要求中的「JSON / DB」，目前這次實際交付的是 JSON 版本。

2.3 《Agent API 規範》

這份文件完成的是 定義 Agent 輸入 / 輸出協議 的要求，並凍結了後續實作所需的最小接口面。

它的作用主要體現在以下幾點：

它是一份 OpenAPI 文件（openapi: 3.1.0），版本為 1.0.0，描述中明確寫明它是 Phase 0 frozen Agent API specification。
它定義了 Phase 0 所需的最小操作接口：
POST /credits/load
POST /data-units/generate
POST /evidence/bind
POST /agents/run
POST /goa/tasks/create
GET /goa/tasks/{task_id}
這些接口建立了從 credit 載入、Data Unit 生成、evidence 綁定、agent 執行到 GOA 任務追蹤的最小流程。
它定義了輸入物件 AgentRequest，包括：
request_id、project_id、agent_type、framework_context、jurisdiction_bundle、target_credit_codes、target_data_unit_ids、evidence_ids、project_stage、run_mode、trace_context。
這些字段構成了 Agent 接收輸入時的正式結構。
它定義了輸出物件 AgentResult，包括：
status、risk_level、reason_codes、evidence_gaps、passed_data_units、failed_data_units、conditional_data_units、explanations、provenance。
這些字段構成了 Agent 評估完成後返回結果的正式結構。

因此，這份文件已經完成了「定義 Agent 輸入 / 輸出協議」的要求，並且把後續階段要依賴的協議邊界凍結下來。



BELUCKS Phase 0 Core Deliverables Mapping （English)

This repository contains the formal Phase 0 delivery package for the BELUCKS / OpenClaw project.
The purpose of Phase 0 is to unify the system language, freeze key abstractions, define the BELUCKS agent boundary, define the Data Unit model, define the Agent input/output protocol, and determine the first supported framework and certification scope. The Phase 0 architecture specification is explicitly marked as Phase 0, frozen, and version 1.0.0. It also states that the document defines the canonical architecture, vocabulary, scope boundary, and agent boundary for the BELUCKS multi-agent building assessment platform.

1. Folder and File Mapping

The three required Phase 0 deliverables are placed under:

01_Core_Deliverables/

They correspond to the following files:

1.1 BELUCKS Architecture Design Document

Folder: 01_Core_Deliverables/
File: BELUCKS_Architecture_Design_Document_v1.0.0.md

1.2 Data Unit Schema

Folder: 01_Core_Deliverables/
File: BELUCKS_Data_Unit_Schema_v1.0.0.json

1.3 Agent API Specification

Folder: 01_Core_Deliverables/
File: BELUCKS_Agent_API_Spec_v1.0.0.yaml

2. How Each Deliverable Satisfies the Phase 0 Requirements
2.1 BELUCKS Architecture Design Document

This file satisfies the Phase 0 requirements related to system language unification, key abstraction freeze, agent responsibility boundary definition, and first supported framework scope definition.

It does so in the following ways:

It defines the canonical vocabulary of the platform across three layers:
Framework Layer (Framework, Category, Credit, Clause),
Assessment Layer (Data Unit, Evidence, Rule Check, Agent Result), and
Platform Layer (GOA Task, Conflict Group, Mapping Target, Project Result).
This directly supports the Phase 0 goal of unifying the system language.
It freezes the architectural scope by clearly defining what is in scope and out of scope for Phase 0.
For example, it explicitly keeps external mapping execution, full certification scoring, real B Agent / E Agent execution, real cross-agent arbitration, platform UI, and full production-form multi-agent orchestration outside the Phase 0 scope.
This is why the document can be considered a real abstraction freeze rather than a high-level concept note.
It defines the BELUCKS agent boundary.
The document states that GOA is responsible for selecting target credits, selecting target agents, preparing data units, passing evidence references, collecting structured results, and generating unified logs.
It also states that a single agent is responsible only for evaluating bound data units and returning structured results, and does not perform total certification rating, cross-agent conflict arbitration, or external framework mapping.
This directly fulfills the requirement to define BELUCKS agent responsibility boundaries.
It defines the first supported framework and certification scope.
The architecture specification identifies BEAM Plus Existing Buildings v3.0 as the only authoritative framework, Management (MAN) as the only priority category, and selects the following pilot credits:
MAN-02-01, MAN-02-02, MAN-02-03, and MAN-03-04.
This fulfills the requirement to determine the first supported framework and certification scope.
2.2 Data Unit Schema

This file satisfies the Phase 0 requirement to define the Data Unit (atomic assessment unit) model and supports the abstraction freeze at the data-model level.

It does so in the following ways:

It is explicitly versioned as data_unit_schema_version: 1.0.0 and marked as frozen, which makes it a formal frozen schema artifact rather than an informal design note.
It defines the identification structure of a Data Unit, including fields such as:
data_unit_id, framework_id, framework_version, credit_code, clause_id, unit_name, and unit_type.
These fields make each Data Unit traceable to a framework, credit, and clause.
It defines the rule structure of a Data Unit, including:
atomic_claim, decision_method, required_evidence_types, endorsement_required, public_disclosure_acceptable, time_window_rule, and buffer_rule.
These fields make the Data Unit a real atomic assessment object rather than only a label or record. They specify what is being judged, how it is judged, and what evidence is required.
It defines tags and multimodal references, including discipline, jurisdiction, time scope, confidence, and references to document, BIM, tabular, API, manual input, geometry, and time series sources.
This supports future execution while keeping the Phase 0 schema generic and extensible.
It reserves fields for future phases, including conflict-resolution-related fields and external mapping fields.
This is important because it allows the Phase 0 schema to remain compatible with later phases such as cross-agent arbitration and external scoring / certification mapping, while still keeping Phase 0 itself focused on frozen structure definition.

Note: in the current Phase 0 delivery package, the Data Unit deliverable is provided in the JSON schema form. The JSON version is the formal schema artifact included in this delivery. This is the concrete deliverable currently supplied under the “JSON / DB” wording of the original requirement.

2.3 Agent API Specification

This file satisfies the Phase 0 requirement to define the Agent input/output protocol and freeze the minimal interface surface for later implementation.

It does so in the following ways:

It is defined as an OpenAPI document (openapi: 3.1.0) with version 1.0.0, and its description explicitly identifies it as the Phase 0 frozen Agent API specification.
It defines the minimal operational endpoints required for the Phase 0 platform flow:
POST /credits/load
POST /data-units/generate
POST /evidence/bind
POST /agents/run
POST /goa/tasks/create
GET /goa/tasks/{task_id}
These endpoints establish the minimum request flow from credit loading to Data Unit generation, evidence binding, agent execution, and GOA task tracking.
It defines the input object AgentRequest, including:
request_id, project_id, agent_type, framework_context, jurisdiction_bundle, target_credit_codes, target_data_unit_ids, evidence_ids, project_stage, run_mode, and trace_context.
This provides the formal structure of what an agent run receives as input.
It defines the output object AgentResult, including:
status, risk_level, reason_codes, evidence_gaps, passed_data_units, failed_data_units, conditional_data_units, explanations, and provenance.
This provides the formal structure of what an agent returns after evaluation.

Because of these elements, this file fulfills the requirement to define the Agent input/output protocol and freeze the protocol boundary needed for later phases.
