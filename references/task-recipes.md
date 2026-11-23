# Agent task recipes

Corpus SHA-256: `64771862f9e1a5135e2f0f36dc95e2eb4d6ca1e675ccd6b248d72f2886d6d887`

These recipes are retrieval and planning evidence. They never authorize API execution.

## `authentication-analyzecontractdrift-apikeyheader` — authentication

How is apiKeyHeader authentication applied to analyzeContractDrift? Cite exactly: operation:analyzeContractDrift, auth:apiKeyHeader

Intent: Recover the exact authentication scheme, location or flow, and required scopes.

Expected evidence:

- operation: `analyzeContractDrift`
- authentication: `apiKeyHeader`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/apiKeyHeader`
- `omniwrap://semantic/operation/analyzeContractDrift`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `authentication-analyzecontractdrift-bearerauth` — authentication

How is bearerAuth authentication applied to analyzeContractDrift? Cite exactly: operation:analyzeContractDrift, auth:bearerAuth

Intent: Recover the exact authentication scheme, location or flow, and required scopes.

Expected evidence:

- operation: `analyzeContractDrift`
- authentication: `bearerAuth`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/bearerAuth`
- `omniwrap://semantic/operation/analyzeContractDrift`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `authentication-collectdeveloperaudit-managedsession` — authentication

How is managedSession authentication applied to collectDeveloperAudit? Cite exactly: operation:collectDeveloperAudit, auth:managedSession

Intent: Recover the exact authentication scheme, location or flow, and required scopes.

Expected evidence:

- operation: `collectDeveloperAudit`
- authentication: `managedSession`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/managedSession`
- `omniwrap://semantic/operation/collectDeveloperAudit`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-analyzecontractdrift` — discovery

Find the exact operation analyzeContractDrift (POST /v1/analysis/contract-drift) for Detect breaking API symbol removals, signature narrowing, and destructive SQL migrations. Cite exactly: operation:analyzeContractDrift, schema:ReviewRequest, auth:apiKeyHeader, auth:bearerAuth

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `analyzeContractDrift`
- schema: `ReviewRequest`
- authentication: `apiKeyHeader`
- authentication: `bearerAuth`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/apiKeyHeader`
- `omniwrap://semantic/auth/bearerAuth`
- `omniwrap://semantic/operation/analyzeContractDrift`
- `omniwrap://semantic/schema/ReviewRequest`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-collectdeveloperaudit` — discovery

Find the exact operation collectDeveloperAudit (POST /cli/managed/developer-audit) for Collect and save a paid repository work audit. Cite exactly: operation:collectDeveloperAudit, schema:DeveloperAuditRequest, auth:managedSession

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `collectDeveloperAudit`
- schema: `DeveloperAuditRequest`
- authentication: `managedSession`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/managedSession`
- `omniwrap://semantic/operation/collectDeveloperAudit`
- `omniwrap://semantic/schema/DeveloperAuditRequest`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-createcodingtask` — discovery

Find the exact operation createCodingTask (POST /v1/tasks) for Create a planned autonomous coding task. Cite exactly: operation:createCodingTask, auth:apiKeyHeader, auth:bearerAuth

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `createCodingTask`
- authentication: `apiKeyHeader`
- authentication: `bearerAuth`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/apiKeyHeader`
- `omniwrap://semantic/auth/bearerAuth`
- `omniwrap://semantic/operation/createCodingTask`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-currentdeveloperidentity` — discovery

Find the exact operation currentDeveloperIdentity (POST /cli/managed/developer-identity) for Read the current verified GitHub identity and authorized source inventory. Cite exactly: operation:currentDeveloperIdentity, schema:ManagedDeveloperIdentity, schema:ManagedDeveloperIdentityRequest, auth:managedSession

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `currentDeveloperIdentity`
- schema: `ManagedDeveloperIdentity`
- schema: `ManagedDeveloperIdentityRequest`
- authentication: `managedSession`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/managedSession`
- `omniwrap://semantic/operation/currentDeveloperIdentity`
- `omniwrap://semantic/schema/ManagedDeveloperIdentity`
- `omniwrap://semantic/schema/ManagedDeveloperIdentityRequest`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-evaluatecompliancegate` — discovery

Find the exact operation evaluateComplianceGate (POST /v1/compliance/gate) for Evaluate changes against SOC2, PCI-DSS, HIPAA, or Standard compliance gates. Cite exactly: operation:evaluateComplianceGate, schema:ComplianceGateRequest, auth:apiKeyHeader, auth:bearerAuth

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `evaluateComplianceGate`
- schema: `ComplianceGateRequest`
- authentication: `apiKeyHeader`
- authentication: `bearerAuth`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/apiKeyHeader`
- `omniwrap://semantic/auth/bearerAuth`
- `omniwrap://semantic/operation/evaluateComplianceGate`
- `omniwrap://semantic/schema/ComplianceGateRequest`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-exportsarif` — discovery

Find the exact operation exportSarif (POST /v1/compliance/sarif) for Export review findings and fixes to OASIS SARIF 2.1.0 format. Cite exactly: operation:exportSarif, auth:apiKeyHeader, auth:bearerAuth

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `exportSarif`
- authentication: `apiKeyHeader`
- authentication: `bearerAuth`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/apiKeyHeader`
- `omniwrap://semantic/auth/bearerAuth`
- `omniwrap://semantic/operation/exportSarif`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-finalizemeteringquota` — discovery

Find the exact operation finalizeMeteringQuota (POST /v1/saas/metering/finalize) for Phase 2 of 3-phase idempotent metering: commit actual review and LLM usage. Cite exactly: operation:finalizeMeteringQuota, auth:apiKeyHeader, auth:bearerAuth

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `finalizeMeteringQuota`
- authentication: `apiKeyHeader`
- authentication: `bearerAuth`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/apiKeyHeader`
- `omniwrap://semantic/auth/bearerAuth`
- `omniwrap://semantic/operation/finalizeMeteringQuota`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-getanalyticsroi` — discovery

Find the exact operation getAnalyticsRoi (GET /v1/analytics/roi) for Compute engineering hours saved and prevented production outage ROI. Cite exactly: operation:getAnalyticsRoi, auth:apiKeyHeader, auth:bearerAuth

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `getAnalyticsRoi`
- authentication: `apiKeyHeader`
- authentication: `bearerAuth`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/apiKeyHeader`
- `omniwrap://semantic/auth/bearerAuth`
- `omniwrap://semantic/operation/getAnalyticsRoi`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-getsaasblueprint` — discovery

Find the exact operation getSaasBlueprint (GET /v1/saas/blueprint) for Retrieve the autonomous SaaS multi-surface adapter blueprint and pricing matrix. Cite exactly: operation:getSaasBlueprint, auth:apiKeyHeader, auth:bearerAuth

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `getSaasBlueprint`
- authentication: `apiKeyHeader`
- authentication: `bearerAuth`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/apiKeyHeader`
- `omniwrap://semantic/auth/bearerAuth`
- `omniwrap://semantic/operation/getSaasBlueprint`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-listcodingtasks` — discovery

Find the exact operation listCodingTasks (GET /v1/tasks) for List autonomous coding tasks. Cite exactly: operation:listCodingTasks, auth:apiKeyHeader, auth:bearerAuth

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `listCodingTasks`
- authentication: `apiKeyHeader`
- authentication: `bearerAuth`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/apiKeyHeader`
- `omniwrap://semantic/auth/bearerAuth`
- `omniwrap://semantic/operation/listCodingTasks`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-reservemeteringquota` — discovery

Find the exact operation reserveMeteringQuota (POST /v1/saas/metering/reserve) for Phase 1 of 3-phase idempotent metering: reserve seat and token quota before execution. Cite exactly: operation:reserveMeteringQuota, auth:apiKeyHeader, auth:bearerAuth

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `reserveMeteringQuota`
- authentication: `apiKeyHeader`
- authentication: `bearerAuth`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/apiKeyHeader`
- `omniwrap://semantic/auth/bearerAuth`
- `omniwrap://semantic/operation/reserveMeteringQuota`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-submitdeveloperevidence` — discovery

Find the exact operation submitDeveloperEvidence (POST /cli/managed/developer-evidence) for Admit revision-linked declarations from the authenticated GitHub user. Cite exactly: operation:submitDeveloperEvidence, schema:DeveloperEvidenceRequest, auth:managedSession

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `submitDeveloperEvidence`
- schema: `DeveloperEvidenceRequest`
- authentication: `managedSession`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/managedSession`
- `omniwrap://semantic/operation/submitDeveloperEvidence`
- `omniwrap://semantic/schema/DeveloperEvidenceRequest`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `error-recovery-collectdeveloperaudit` — error-recovery

Which failure responses and error schemas apply to collectDeveloperAudit? Cite exactly: operation:collectDeveloperAudit, auth:managedSession

Intent: Recover non-success response selectors and their declared error payloads.

Expected evidence:

- operation: `collectDeveloperAudit`
- authentication: `managedSession`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/managedSession`
- `omniwrap://semantic/operation/collectDeveloperAudit`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `error-recovery-currentdeveloperidentity` — error-recovery

Which failure responses and error schemas apply to currentDeveloperIdentity? Cite exactly: operation:currentDeveloperIdentity, auth:managedSession

Intent: Recover non-success response selectors and their declared error payloads.

Expected evidence:

- operation: `currentDeveloperIdentity`
- authentication: `managedSession`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/managedSession`
- `omniwrap://semantic/operation/currentDeveloperIdentity`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `error-recovery-submitdeveloperevidence` — error-recovery

Which failure responses and error schemas apply to submitDeveloperEvidence? Cite exactly: operation:submitDeveloperEvidence, auth:managedSession

Intent: Recover non-success response selectors and their declared error payloads.

Expected evidence:

- operation: `submitDeveloperEvidence`
- authentication: `managedSession`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/managedSession`
- `omniwrap://semantic/operation/submitDeveloperEvidence`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-analyzecontractdrift` — integration

Plan a correct SDK integration for analyzeContractDrift (POST /v1/analysis/contract-drift). Cite exactly: operation:analyzeContractDrift, schema:ReviewRequest, auth:apiKeyHeader, auth:bearerAuth

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `analyzeContractDrift`
- schema: `ReviewRequest`
- authentication: `apiKeyHeader`
- authentication: `bearerAuth`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/apiKeyHeader`
- `omniwrap://semantic/auth/bearerAuth`
- `omniwrap://semantic/operation/analyzeContractDrift`
- `omniwrap://semantic/schema/ReviewRequest`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-collectdeveloperaudit` — integration

Plan a correct SDK integration for collectDeveloperAudit (POST /cli/managed/developer-audit). Cite exactly: operation:collectDeveloperAudit, schema:DeveloperAuditRequest, auth:managedSession

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `collectDeveloperAudit`
- schema: `DeveloperAuditRequest`
- authentication: `managedSession`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/managedSession`
- `omniwrap://semantic/operation/collectDeveloperAudit`
- `omniwrap://semantic/schema/DeveloperAuditRequest`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-createcodingtask` — integration

Plan a correct SDK integration for createCodingTask (POST /v1/tasks). Cite exactly: operation:createCodingTask, auth:apiKeyHeader, auth:bearerAuth

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `createCodingTask`
- authentication: `apiKeyHeader`
- authentication: `bearerAuth`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/apiKeyHeader`
- `omniwrap://semantic/auth/bearerAuth`
- `omniwrap://semantic/operation/createCodingTask`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-currentdeveloperidentity` — integration

Plan a correct SDK integration for currentDeveloperIdentity (POST /cli/managed/developer-identity). Cite exactly: operation:currentDeveloperIdentity, schema:ManagedDeveloperIdentity, schema:ManagedDeveloperIdentityRequest, auth:managedSession

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `currentDeveloperIdentity`
- schema: `ManagedDeveloperIdentity`
- schema: `ManagedDeveloperIdentityRequest`
- authentication: `managedSession`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/managedSession`
- `omniwrap://semantic/operation/currentDeveloperIdentity`
- `omniwrap://semantic/schema/ManagedDeveloperIdentity`
- `omniwrap://semantic/schema/ManagedDeveloperIdentityRequest`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-evaluatecompliancegate` — integration

Plan a correct SDK integration for evaluateComplianceGate (POST /v1/compliance/gate). Cite exactly: operation:evaluateComplianceGate, schema:ComplianceGateRequest, auth:apiKeyHeader, auth:bearerAuth

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `evaluateComplianceGate`
- schema: `ComplianceGateRequest`
- authentication: `apiKeyHeader`
- authentication: `bearerAuth`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/apiKeyHeader`
- `omniwrap://semantic/auth/bearerAuth`
- `omniwrap://semantic/operation/evaluateComplianceGate`
- `omniwrap://semantic/schema/ComplianceGateRequest`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-exportsarif` — integration

Plan a correct SDK integration for exportSarif (POST /v1/compliance/sarif). Cite exactly: operation:exportSarif, auth:apiKeyHeader, auth:bearerAuth

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `exportSarif`
- authentication: `apiKeyHeader`
- authentication: `bearerAuth`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/apiKeyHeader`
- `omniwrap://semantic/auth/bearerAuth`
- `omniwrap://semantic/operation/exportSarif`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-finalizemeteringquota` — integration

Plan a correct SDK integration for finalizeMeteringQuota (POST /v1/saas/metering/finalize). Cite exactly: operation:finalizeMeteringQuota, auth:apiKeyHeader, auth:bearerAuth

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `finalizeMeteringQuota`
- authentication: `apiKeyHeader`
- authentication: `bearerAuth`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/apiKeyHeader`
- `omniwrap://semantic/auth/bearerAuth`
- `omniwrap://semantic/operation/finalizeMeteringQuota`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-getanalyticsroi` — integration

Plan a correct SDK integration for getAnalyticsRoi (GET /v1/analytics/roi). Cite exactly: operation:getAnalyticsRoi, auth:apiKeyHeader, auth:bearerAuth

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `getAnalyticsRoi`
- authentication: `apiKeyHeader`
- authentication: `bearerAuth`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/apiKeyHeader`
- `omniwrap://semantic/auth/bearerAuth`
- `omniwrap://semantic/operation/getAnalyticsRoi`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-getsaasblueprint` — integration

Plan a correct SDK integration for getSaasBlueprint (GET /v1/saas/blueprint). Cite exactly: operation:getSaasBlueprint, auth:apiKeyHeader, auth:bearerAuth

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `getSaasBlueprint`
- authentication: `apiKeyHeader`
- authentication: `bearerAuth`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/apiKeyHeader`
- `omniwrap://semantic/auth/bearerAuth`
- `omniwrap://semantic/operation/getSaasBlueprint`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-listcodingtasks` — integration

Plan a correct SDK integration for listCodingTasks (GET /v1/tasks). Cite exactly: operation:listCodingTasks, auth:apiKeyHeader, auth:bearerAuth

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `listCodingTasks`
- authentication: `apiKeyHeader`
- authentication: `bearerAuth`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/apiKeyHeader`
- `omniwrap://semantic/auth/bearerAuth`
- `omniwrap://semantic/operation/listCodingTasks`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-reservemeteringquota` — integration

Plan a correct SDK integration for reserveMeteringQuota (POST /v1/saas/metering/reserve). Cite exactly: operation:reserveMeteringQuota, auth:apiKeyHeader, auth:bearerAuth

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `reserveMeteringQuota`
- authentication: `apiKeyHeader`
- authentication: `bearerAuth`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/apiKeyHeader`
- `omniwrap://semantic/auth/bearerAuth`
- `omniwrap://semantic/operation/reserveMeteringQuota`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-submitdeveloperevidence` — integration

Plan a correct SDK integration for submitDeveloperEvidence (POST /cli/managed/developer-evidence). Cite exactly: operation:submitDeveloperEvidence, schema:DeveloperEvidenceRequest, auth:managedSession

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `submitDeveloperEvidence`
- schema: `DeveloperEvidenceRequest`
- authentication: `managedSession`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/managedSession`
- `omniwrap://semantic/operation/submitDeveloperEvidence`
- `omniwrap://semantic/schema/DeveloperEvidenceRequest`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.
