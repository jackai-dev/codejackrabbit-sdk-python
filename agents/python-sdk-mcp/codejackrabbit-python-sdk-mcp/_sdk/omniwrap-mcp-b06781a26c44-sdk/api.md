# CodeJackRabbit Python API

<!-- omniwrap-api-reference eyJjb250cmFjdF9maW5nZXJwcmludCI6ImIwNjc4MWEyNmM0NDY5ZThmMTI4MzBhMDRkNDU1OTU3YmY2MjBkNDJiOWUxZGYxNTVlOTNlZTAwZjI5M2QxYzkiLCJvcGVyYXRpb25fY291bnQiOjI4LCJyZW5kZXJlciI6InB5dGhvbiIsInZlcnNpb24iOiIxLjUuMCJ9 -->

This generated index is tied to Semantic IR `1.14.0` and contract fingerprint `b06781a26c4469e8f12830a04d455957bf620d42b9e1df155e93ee00f293d1c9`. Every operation below is rendered from the same semantic contract and artifact-attested public member allocation as the SDK.

SDK maturity: **experimental**  
Artifact evidence: [`omniwrap-artifact.json`](omniwrap-artifact.json) binds this file by SHA-256 and is revalidated by the package gate.

## Client hooks and tracing

`Client(hooks=Hooks(...))` registers four callbacks. Every attempt starts with `before_request` and ends with exactly one of `on_retry` (another attempt follows), `after_response` (the success the call returns) or `on_error` (the failure the call reports). Each receives the operation id, the HTTP method, the URL, the request headers, the attempt number (from 1), the time elapsed since the call started and, once the server answered, the HTTP status. No context carries a credential: `Authorization`, `Proxy-Authorization`, `Cookie`, every API-key header and API-key query parameter, and any configured credential value read `[redacted]`. Every context is a frozen `HookContext`: no hook can change the request.

`Client(tracer=...)` opens one span per call through the tracer interface this SDK defines, named after the operation id, with `http.request.method`, `http.response.status_code` and `http.request.resend_count`. It needs no tracing library; README.md maps it onto the OpenTelemetry API.

## Shared types

- `AuditContextRequest`
- `AuditSnapshotsRequest`
- `ComplianceGateRequest`
- `DeveloperAuditRequest`
- `DeveloperEvidenceRequest`
- `FileChange`
- `FinOpsRequest`
- `ManagedDeveloperIdentity`
- `ManagedDeveloperIdentityRequest`
- `ReviewRequest`
- `WaitlistRequest`

## Resource `analysis`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXNpcy5hbmFseXplX2NvbnRyYWN0X2RyaWZ0IiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImFuYWx5emVDb250cmFjdERyaWZ0IiwicGF0aCI6Ii92MS9hbmFseXNpcy9jb250cmFjdC1kcmlmdCIsInJlc291cmNlIjoiYW5hbHlzaXMiLCJzZWN0aW9uX3NoYTI1NiI6ImExOGY1Nzk4YWNlNzZiODMzMTIyMmY1ZDY0YmMwMTgyOGNlMGE2MjU4Mjk5ZmY4NWZlNTE3MjYzYTg5ZTEyYTciLCJzaWduYXR1cmVfc2hhMjU2IjoiNWI0NDljMzBkOTAwMWYyNDYzZTc5ZmM4NGNkOTZjNzAwOGZjYWFhN2FjZjllMGNhNzE2OGQzNTJkNjEwMzgzZiJ9 -->
### `client.analysis.analyze_contract_drift`

Operation ID: `analyzeContractDrift`  
Route: `POST` `/v1/analysis/contract-drift`  
Equivalent member: `client.analyze_contract_drift`  

#### Signature

```python
client.analysis.analyze_contract_drift(body: ReviewRequest, *, content_type: Optional[str] = None, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> None
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Contract drift report and SemVer recommendation | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.analysis.analyze_contract_drift({'files': [{'filename': 'example'}]}, content_type='application/json')
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJhbmFseXplQ29udHJhY3REcmlmdCJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXNpcy5hbmFseXplX3BlcmZfZmluX29wcyIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJhbmFseXplUGVyZkZpbk9wcyIsInBhdGgiOiIvdjEvYW5hbHlzaXMvcGVyZi1maW5vcHMiLCJyZXNvdXJjZSI6ImFuYWx5c2lzIiwic2VjdGlvbl9zaGEyNTYiOiJjZmZiZTBlZmZhZDdhNjIxMGMzMWMxMjkxOGNlMWZjOWZlMjc5OTYxYzYwNjQ1OTdhOWNmZmRjNTFhMjVmYzUzIiwic2lnbmF0dXJlX3NoYTI1NiI6IjQ0MTllYTQ2MWZhMWFmYmVhNDA4NTJhYjhjZjUxOWMyMTNjODYwMTkyY2YyYjlkYzNmNzg2ZGZmMzY2M2JiZGMifQ -->
### `client.analysis.analyze_perf_fin_ops`

Operation ID: `analyzePerfFinOps`  
Route: `POST` `/v1/analysis/perf-finops`  
Equivalent member: `client.analyze_perf_fin_ops`  

#### Signature

```python
client.analysis.analyze_perf_fin_ops(body: ReviewRequest, *, content_type: Optional[str] = None, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> None
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Performance and FinOps audit report | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.analysis.analyze_perf_fin_ops({'files': [{'filename': 'example'}]}, content_type='application/json')
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJhbmFseXplUGVyZkZpbk9wcyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXNpcy5wbGFuX3N0YWNrZWRfcHJfc3BsaXQiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicGxhblN0YWNrZWRQclNwbGl0IiwicGF0aCI6Ii92MS9hbmFseXNpcy9zcGxpdC1wciIsInJlc291cmNlIjoiYW5hbHlzaXMiLCJzZWN0aW9uX3NoYTI1NiI6IjE5MWRmMDAxNjM4MWI0OWFlM2ZkMWNiZGMwM2U0ZDA0YThhYTBmYTkyZTY2ODMyZGNmYzExNDQ3ZjY3NGFiZmQiLCJzaWduYXR1cmVfc2hhMjU2IjoiZDk4NDg2MWI1OWRlNGMyZjQyMzE5NTJkZTg5MjRjMmE5YTUyYjkyZTE3MzI1M2Y4NDhlMDg4NThiNGQyYjU5NiJ9 -->
### `client.analysis.plan_stacked_pr_split`

Operation ID: `planStackedPrSplit`  
Route: `POST` `/v1/analysis/split-pr`  
Equivalent member: `client.plan_stacked_pr_split`  

#### Signature

```python
client.analysis.plan_stacked_pr_split(body: ReviewRequest, *, content_type: Optional[str] = None, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> None
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Ordered stacked PR plan and git commands | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.analysis.plan_stacked_pr_split({'files': [{'filename': 'example'}]}, content_type='application/json')
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJwbGFuU3RhY2tlZFByU3BsaXQifQ -->

## Resource `analytics`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXRpY3MuZ2V0X3JvaSIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEFuYWx5dGljc1JvaSIsInBhdGgiOiIvdjEvYW5hbHl0aWNzL3JvaSIsInJlc291cmNlIjoiYW5hbHl0aWNzIiwic2VjdGlvbl9zaGEyNTYiOiJmMWZkMzE5MTBjNmNhOGM5ZTllMjZlOWE1OGViMGZlYjAzZmYxMDVjNTRmMjMwNzI0ZTczYTUzZGY5Y2FlOWJmIiwic2lnbmF0dXJlX3NoYTI1NiI6ImRhMDZkNDk5Y2VmMjJhZWRlY2E5MmZlMzEzY2ZlMDZmNTNjNjQxOTEwNDhlNzc2NmMzY2ZlOWVmYmQyYmE3MTEifQ -->
### `client.analytics.get_roi`

Operation ID: `getAnalyticsRoi`  
Route: `GET` `/v1/analytics/roi`  
Equivalent member: `client.get_analytics_roi`  

#### Signature

```python
client.analytics.get_roi(*, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> None
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | ROI telemetry summary | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.analytics.get_roi()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRBbmFseXRpY3NSb2kifQ -->

## Resource `capabilities`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJjYXBhYmlsaXRpZXMuZ2V0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0Q2FwYWJpbGl0aWVzIiwicGF0aCI6Ii92MS9jYXBhYmlsaXRpZXMiLCJyZXNvdXJjZSI6ImNhcGFiaWxpdGllcyIsInNlY3Rpb25fc2hhMjU2IjoiYmZjZTcxYjJiODM2NTY5NmE0NzI0ZDk3NzZkMWVlYjEyYzQxMDU1YWE3YTAzNmZhMjQyNTBhMmRkNDdiMzkxOCIsInNpZ25hdHVyZV9zaGEyNTYiOiIzMDUxM2Y5OGI2MjBmOTZmNDkyMGE0YmZiMmQ5OWZiZWQxMmNhYWM2YTc5NmFiNjY1MmU5MDFlZDZlZmQwMWEzIn0 -->
### `client.capabilities.get`

Operation ID: `getCapabilities`  
Route: `GET` `/v1/capabilities`  
Equivalent member: `client.get_capabilities`  

#### Signature

```python
client.capabilities.get(*, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> None
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Capabilities catalog | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.capabilities.get()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRDYXBhYmlsaXRpZXMifQ -->

## Resource `compliance`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJjb21wbGlhbmNlLmV2YWx1YXRlX2dhdGUiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiZXZhbHVhdGVDb21wbGlhbmNlR2F0ZSIsInBhdGgiOiIvdjEvY29tcGxpYW5jZS9nYXRlIiwicmVzb3VyY2UiOiJjb21wbGlhbmNlIiwic2VjdGlvbl9zaGEyNTYiOiIwZTYzMTdlMzk3YmQxNWUzYWVlOGQzMTk5OGQ3NDQ5ZTQ1NWQzNGE3Y2M3NDBkNGMyYmUzNTgzODZjYWE0YzkzIiwic2lnbmF0dXJlX3NoYTI1NiI6IjY2YjA1NzQyODhmYjNiZjYyNDA5NWY0NDNmMGVlYTc2YzJkZjVjOTE2ZDBhMmNjY2JiZDZhMTcwYmE5MzU2NDgifQ -->
### `client.compliance.evaluate_gate`

Operation ID: `evaluateComplianceGate`  
Route: `POST` `/v1/compliance/gate`  
Equivalent member: `client.evaluate_compliance_gate`  

#### Signature

```python
client.compliance.evaluate_gate(body: ComplianceGateRequest, *, content_type: Optional[str] = None, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> None
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ComplianceGateRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Compliance gate verdict and SHA-256 attestation | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.compliance.evaluate_gate({}, content_type='application/json')
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJldmFsdWF0ZUNvbXBsaWFuY2VHYXRlIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJjb21wbGlhbmNlLmV4cG9ydF9zYXJpZiIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJleHBvcnRTYXJpZiIsInBhdGgiOiIvdjEvY29tcGxpYW5jZS9zYXJpZiIsInJlc291cmNlIjoiY29tcGxpYW5jZSIsInNlY3Rpb25fc2hhMjU2IjoiYTVhNDg1MmZmYmM0YTI5YTBmNTY2NTYwOWE5MGZkOWQwNDBhMWFlNDUyMGNmOTVkZmU4NjExY2IzZTgxY2YyZiIsInNpZ25hdHVyZV9zaGEyNTYiOiI3ODFiNmQ5NTUzNWFlYTY5MjRiOGNjMjE5YzE4ODU4OGJkM2FkOTcxNDA4MDFhOGE1MTA1M2Y5ZmY3YTJmYmJjIn0 -->
### `client.compliance.export_sarif`

Operation ID: `exportSarif`  
Route: `POST` `/v1/compliance/sarif`  
Equivalent member: `client.export_sarif`  

#### Signature

```python
client.compliance.export_sarif(body: dict[str, Any], *, content_type: Optional[str] = None, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> None
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | SARIF 2.1.0 JSON document | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.compliance.export_sarif({}, content_type='application/json')
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJleHBvcnRTYXJpZiJ9 -->

## Resource `developer_intelligence`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJkZXZlbG9wZXJfaW50ZWxsaWdlbmNlLmNvbGxlY3RfYXVkaXQiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiY29sbGVjdERldmVsb3BlckF1ZGl0IiwicGF0aCI6Ii9jbGkvbWFuYWdlZC9kZXZlbG9wZXItYXVkaXQiLCJyZXNvdXJjZSI6ImRldmVsb3Blcl9pbnRlbGxpZ2VuY2UiLCJzZWN0aW9uX3NoYTI1NiI6IjM4YTkzMzAzMDBhYmNmYTVjYzNlZGIyNGY5Y2FhMzQ1MmU5MDAxY2Q2ZjQ2NTNmNjQ1NDUxNDZiNTg5NzNiZDUiLCJzaWduYXR1cmVfc2hhMjU2IjoiYWM1ZmFkOGQ5YTZlMjg2MWM2YTI4YjgwZDZiN2Q2YTI5MTVhMzNmZTRkMzkxY2E1N2VjNDI0OWYwODFmNWMxZSJ9 -->
### `client.developer_intelligence.collect_audit`

Operation ID: `collectDeveloperAudit`  
Route: `POST` `/cli/managed/developer-audit`  
Equivalent member: `client.collect_developer_audit`  

#### Signature

```python
client.developer_intelligence.collect_audit(body: DeveloperAuditRequest, *, content_type: Optional[str] = None, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> dict[str, Any]
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `DeveloperAuditRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Versioned report with source coverage, missing evidence and immutable snapshot reference. | application/json (object) |
| `default` | Explicit authentication, paid access, source authorization, capacity or collection blocker. | none |

#### Canonical required-input example

```json
{
  "body": {
    "from": "2026-01-09",
    "repositoryId": "1",
    "to": "2026-01-18"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.developer_intelligence.collect_audit({'from': '2026-01-09', 'repositoryId': '1', 'to': '2026-01-18'}, content_type='application/json')
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjb2xsZWN0RGV2ZWxvcGVyQXVkaXQifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJkZXZlbG9wZXJfaW50ZWxsaWdlbmNlLmN1cnJlbnRfaWRlbnRpdHkiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiY3VycmVudERldmVsb3BlcklkZW50aXR5IiwicGF0aCI6Ii9jbGkvbWFuYWdlZC9kZXZlbG9wZXItaWRlbnRpdHkiLCJyZXNvdXJjZSI6ImRldmVsb3Blcl9pbnRlbGxpZ2VuY2UiLCJzZWN0aW9uX3NoYTI1NiI6IjkxOWNiYTZjNThjZjE1ZTBkZjg5Y2EyZTkzYzY1NDE2ZmQ4YjMyN2VkNDFiMTFmNTM5NDYzNzU1ODc5Mjk0OTAiLCJzaWduYXR1cmVfc2hhMjU2IjoiYzg2NmQzOTJlOGI0MGNjZWRmNGJmMGE0YzY0MzcwYWZlM2RkMzVkMWE0MjhmMWFkMWQ3NjBhNDM4ZDcwOWM2MSJ9 -->
### `client.developer_intelligence.current_identity`

Operation ID: `currentDeveloperIdentity`  
Route: `POST` `/cli/managed/developer-identity`  
Equivalent member: `client.current_developer_identity`  

#### Signature

```python
client.developer_intelligence.current_identity(body: ManagedDeveloperIdentityRequest, *, content_type: Optional[str] = None, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> ManagedDeveloperIdentity
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ManagedDeveloperIdentityRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Current verified identity and authorized repositories. | application/json (ManagedDeveloperIdentity) |
| `default` | Explicit account, GitHub identity or source authorization blocker. | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.developer_intelligence.current_identity({}, content_type='application/json')
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjdXJyZW50RGV2ZWxvcGVySWRlbnRpdHkifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJkZXZlbG9wZXJfaW50ZWxsaWdlbmNlLmRlY2xhcmVfcHJvamVjdF9jb250ZXh0IiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImRlY2xhcmVEZXZlbG9wZXJQcm9qZWN0Q29udGV4dCIsInBhdGgiOiIvY2xpL21hbmFnZWQvYXVkaXQtY29udGV4dCIsInJlc291cmNlIjoiZGV2ZWxvcGVyX2ludGVsbGlnZW5jZSIsInNlY3Rpb25fc2hhMjU2IjoiNWVjYjg1ODc0ZWQ3MDdjNWY3YmQ2NjUzMmRhY2JmMzQ0OWFiODRkM2Q5OWZhN2ZlNmFlMmU5OWFmN2JhNTA2OSIsInNpZ25hdHVyZV9zaGEyNTYiOiIxODQ4YTFkYWI1ZGY0MzdhZjJkMzhmMDYwNWFiMjc2OWQ2MjUzOGE4NWM1YmEyNzM2ZmUzOTY2ZGMxNWU3OGVhIn0 -->
### `client.developer_intelligence.declare_project_context`

Operation ID: `declareDeveloperProjectContext`  
Route: `POST` `/cli/managed/audit-context`  
Equivalent member: `client.declare_developer_project_context`  

#### Signature

```python
client.developer_intelligence.declare_project_context(body: AuditContextRequest, *, content_type: Optional[str] = None, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> dict[str, Any]
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `AuditContextRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Immutable declaration or correction receipt. | application/json (object) |
| `default` | Explicit authorization, contributor identity, correction or storage capacity blocker. | none |

#### Canonical required-input example

```json
{
  "body": {
    "declaration": {
      "contributorId": "1",
      "effectiveFrom": "2026-01-02",
      "effectiveTo": "2026-01-11",
      "snapshotId": "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "source": "example",
      "supersedes": "example",
      "type": "project_join",
      "value": "example"
    },
    "repositoryId": "1"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.developer_intelligence.declare_project_context({'declaration': {'contributorId': '1', 'effectiveFrom': '2026-01-02', 'effectiveTo': '2026-01-11', 'snapshotId': 'aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa', 'source': 'example', 'supersedes': 'example', 'type': 'project_join', 'value': 'example'}, 'repositoryId': '1'}, content_type='application/json')
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJkZWNsYXJlRGV2ZWxvcGVyUHJvamVjdENvbnRleHQifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJkZXZlbG9wZXJfaW50ZWxsaWdlbmNlLm1hbmFnZWRfYXVkaXRfc25hcHNob3RzIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6Im1hbmFnZWRBdWRpdFNuYXBzaG90cyIsInBhdGgiOiIvY2xpL21hbmFnZWQvYXVkaXQtc25hcHNob3RzIiwicmVzb3VyY2UiOiJkZXZlbG9wZXJfaW50ZWxsaWdlbmNlIiwic2VjdGlvbl9zaGEyNTYiOiJlZGUyMmE5NjY5MGMzN2FkYzI3NGUwZmU3ZDIzOGRlYzdlMWMzMTY3MzBiYzE4MzczMzM4NzUyYTU3OWQ1ZWQzIiwic2lnbmF0dXJlX3NoYTI1NiI6IjQ0YjcxMmZjNTcxNmQ0YTY2ZDA3ZjMzZTI3MTkyMjNkNmNlZDFmNjBkNzUwZDA2YjQzODIzODlhYTQyNjQzMjUifQ -->
### `client.developer_intelligence.managed_audit_snapshots`

Operation ID: `managedAuditSnapshots`  
Route: `POST` `/cli/managed/audit-snapshots`  
Equivalent member: `client.managed_audit_snapshots`  

#### Signature

```python
client.developer_intelligence.managed_audit_snapshots(body: AuditSnapshotsRequest, *, content_type: Optional[str] = None, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> dict[str, Any]
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `AuditSnapshotsRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Snapshot list or digest-verified immutable envelope. | application/json (object) |
| `default` | Explicit authorization, expiry, missing snapshot or integrity blocker. | none |

#### Canonical required-input example

```json
{
  "body": {
    "action": "list",
    "repositoryId": "1"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.developer_intelligence.managed_audit_snapshots({'action': 'list', 'repositoryId': '1'}, content_type='application/json')
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJtYW5hZ2VkQXVkaXRTbmFwc2hvdHMifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJkZXZlbG9wZXJfaW50ZWxsaWdlbmNlLnByb3ZpZGVyX2Nvc3RfZXZpZGVuY2UiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicHJvdmlkZXJDb3N0RXZpZGVuY2UiLCJwYXRoIjoiL2NsaS9tYW5hZ2VkL2Zpbm9wcyIsInJlc291cmNlIjoiZGV2ZWxvcGVyX2ludGVsbGlnZW5jZSIsInNlY3Rpb25fc2hhMjU2IjoiNDA1Y2E5NGI1OWZiM2QxOWEyZjg0ZDc3MGMyMzQ4NzZhZWZmY2M5YTZmY2U5YTkyNjBhM2FjNWM0M2QyZjE1MSIsInNpZ25hdHVyZV9zaGEyNTYiOiI2YjdiZmZiMzg4ZDA0ODgwYmU2NDdhNWQ4MzUzYTA5YWMyN2E1Yzc5MzQxNjY5MzBjYWFhZjI1ZWJiODNlNzAyIn0 -->
### `client.developer_intelligence.provider_cost_evidence`

Operation ID: `providerCostEvidence`  
Route: `POST` `/cli/managed/finops`  
Equivalent member: `client.provider_cost_evidence`  

#### Signature

```python
client.developer_intelligence.provider_cost_evidence(body: FinOpsRequest, *, content_type: Optional[str] = None, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> dict[str, Any]
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `FinOpsRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Server report or declaration receipt. Unknown costs remain null. | application/json (object) |
| `default` | Explicit permission, paid access, source or declaration validation blocker. | none |

#### Canonical required-input example

```json
{
  "body": {
    "action": "report"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.developer_intelligence.provider_cost_evidence({'action': 'report'}, content_type='application/json')
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJwcm92aWRlckNvc3RFdmlkZW5jZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJkZXZlbG9wZXJfaW50ZWxsaWdlbmNlLnN1Ym1pdF9ldmlkZW5jZSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJzdWJtaXREZXZlbG9wZXJFdmlkZW5jZSIsInBhdGgiOiIvY2xpL21hbmFnZWQvZGV2ZWxvcGVyLWV2aWRlbmNlIiwicmVzb3VyY2UiOiJkZXZlbG9wZXJfaW50ZWxsaWdlbmNlIiwic2VjdGlvbl9zaGEyNTYiOiJiM2QxN2IzNGVjYWVlMjU5YjJkMjk0NzdlMzc0NGE0ZDExMzQyNmM0NWY5NmFmOWU4YzRiYTI0YzAzNTc2NmI3Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjIwN2NiOWE3ZDU3MzM3ZjljZmViNWE1NTdlOGU1MmVlNjZmNTgzM2MzNTVlNDQ2ODUyNWIxNjUwMWQ5YTExYTcifQ -->
### `client.developer_intelligence.submit_evidence`

Operation ID: `submitDeveloperEvidence`  
Route: `POST` `/cli/managed/developer-evidence`  
Equivalent member: `client.submit_developer_evidence`  

#### Signature

```python
client.developer_intelligence.submit_evidence(body: DeveloperEvidenceRequest, *, content_type: Optional[str] = None, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> dict[str, Any]
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `DeveloperEvidenceRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Accepted and duplicate span counts. | application/json (object) |
| `default` | Explicit identity, repository, paid access or evidence validation blocker. | none |

#### Canonical required-input example

```json
{
  "body": {
    "category": "coding",
    "input": {},
    "repositoryId": "1"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.developer_intelligence.submit_evidence({'category': 'coding', 'input': {}, 'repositoryId': '1'}, content_type='application/json')
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzdWJtaXREZXZlbG9wZXJFdmlkZW5jZSJ9 -->

## Resource `health`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJoZWFsdGguZ2V0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0SGVhbHRoIiwicGF0aCI6Ii9oZWFsdGgiLCJyZXNvdXJjZSI6ImhlYWx0aCIsInNlY3Rpb25fc2hhMjU2IjoiZTFiMDc3ZjRmM2UwNjhjNjcxOTYzOGNjYWE0NTI4ODhiZDkwZGE5YTU2YzU0Yjg2MzllZDllZGYzMWM5OWRhNSIsInNpZ25hdHVyZV9zaGEyNTYiOiIxOWRiZmQ0MTM1N2I1ZWZlNzVhNjU5YzA5ZjNiNWU5ZjY5YWY0YzUwNDViNTJiZGM5NmRjNzNlN2QzNjkzNWM0In0 -->
### `client.health.get`

Operation ID: `getHealth`  
Route: `GET` `/health`  
Equivalent member: `client.get_health`  

#### Signature

```python
client.health.get(*, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> None
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Server health status | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.health.get()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRIZWFsdGgifQ -->

## Resource `reviews`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJyZXZpZXdzLmJ1aWxkX2F1dG9maXhfYnVuZGxlIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImJ1aWxkQXV0b2ZpeEJ1bmRsZSIsInBhdGgiOiIvdjEvcmV2aWV3cy9hdXRvZml4IiwicmVzb3VyY2UiOiJyZXZpZXdzIiwic2VjdGlvbl9zaGEyNTYiOiI1MDMwZjNkZjBiMTg1NWZiYWM3YzRkNmYwMDdkZDhkYzg4YzQ2NTI2YjI0OGUxMDRmZTNlZjJkYmE3OTQwZmRjIiwic2lnbmF0dXJlX3NoYTI1NiI6IjdjNTg1MzM0MjEyYmI1MDZmNzFkYjM2NGZjMjM4ODBmMWViYjQ2MjgzMGNlOGQ4YzZjYjdmM2ZmY2UzMmJiNzIifQ -->
### `client.reviews.build_autofix_bundle`

Operation ID: `buildAutofixBundle`  
Route: `POST` `/v1/reviews/autofix`  
Equivalent member: `client.build_autofix_bundle`  

#### Signature

```python
client.reviews.build_autofix_bundle(body: ReviewRequest, *, content_type: Optional[str] = None, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> None
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Remediation patch bundle | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.reviews.build_autofix_bundle({'files': [{'filename': 'example'}]}, content_type='application/json')
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJidWlsZEF1dG9maXhCdW5kbGUifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJyZXZpZXdzLmNvbXB1dGVfcmlza19yYWRhciIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJjb21wdXRlUmlza1JhZGFyIiwicGF0aCI6Ii92MS9yZXZpZXdzL3Jpc2stcmFkYXIiLCJyZXNvdXJjZSI6InJldmlld3MiLCJzZWN0aW9uX3NoYTI1NiI6IjJhYmI2Nzg4ZjI4Yzg0Yzk5NTlmYmNiNDRmZGNjNTg1ZTM0NDk4MzdmN2NjYWY2OTQ2ZTYxMjNiODliYmJjMTMiLCJzaWduYXR1cmVfc2hhMjU2IjoiMDAwZGEzOWJhYzE0ZTExODcwNWQ4NTJiY2U5MGJhNTY1ZThiODI1MjMzZDZmMDRhYzA0YjY0NGNlMzg3MTEyZSJ9 -->
### `client.reviews.compute_risk_radar`

Operation ID: `computeRiskRadar`  
Route: `POST` `/v1/reviews/risk-radar`  
Equivalent member: `client.compute_risk_radar`  

#### Signature

```python
client.reviews.compute_risk_radar(body: ReviewRequest, *, content_type: Optional[str] = None, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> None
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | 6-axis Risk Radar telemetry | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.reviews.compute_risk_radar({'files': [{'filename': 'example'}]}, content_type='application/json')
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjb21wdXRlUmlza1JhZGFyIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJyZXZpZXdzLmNyZWF0ZSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJjcmVhdGVSZXZpZXciLCJwYXRoIjoiL3YxL3Jldmlld3MiLCJyZXNvdXJjZSI6InJldmlld3MiLCJzZWN0aW9uX3NoYTI1NiI6ImU0ZmMwZDFmZGMzZTQ1NTg2ZTU2MDI5NmQ5ZTYzZjk4NjBiZDI2Y2EzZjE3ZWI5NGRkZDg0MDVlYzg1NzhlZjQiLCJzaWduYXR1cmVfc2hhMjU2IjoiMDdkZjRlMWQ0NTE4MzQ0ZGE0ZjRkZDNhMDU1NDYyM2RlZTQxZDdlNDllOTI2NWQ5ODhjOTlmZjUyNDg3NWI5MiJ9 -->
### `client.reviews.create`

Operation ID: `createReview`  
Route: `POST` `/v1/reviews`  
Equivalent member: `client.create_review`  

#### Signature

```python
client.reviews.create(body: ReviewRequest, *, content_type: Optional[str] = None, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> None
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Completed review result with findings, blast radius, and change stack | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.reviews.create({'files': [{'filename': 'example'}]}, content_type='application/json')
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVSZXZpZXcifQ -->

## Resource `saas`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLmZpbmFsaXplX21ldGVyaW5nX3F1b3RhIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImZpbmFsaXplTWV0ZXJpbmdRdW90YSIsInBhdGgiOiIvdjEvc2Fhcy9tZXRlcmluZy9maW5hbGl6ZSIsInJlc291cmNlIjoic2FhcyIsInNlY3Rpb25fc2hhMjU2IjoiOTBmMDJjYjZiN2RjMWI2NzM3MzIyM2QxOThlOWE0ZmFjMzVhZGFkYTllN2JkZmE3YjlhYjZmOTI1MTgyMmQ4ZSIsInNpZ25hdHVyZV9zaGEyNTYiOiI1YjI3NGQwYzYyMTAzMDBkM2I0NzE0NWYxNGQ5NTM4MGJjYzYzMDVkN2I3OWZiZjZkMzNjMjQzYmJmZGFmYjRiIn0 -->
### `client.saas.finalize_metering_quota`

Operation ID: `finalizeMeteringQuota`  
Route: `POST` `/v1/saas/metering/finalize`  
Equivalent member: `client.finalize_metering_quota`  

#### Signature

```python
client.saas.finalize_metering_quota(body: dict[str, Any], *, content_type: Optional[str] = None, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> None
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Finalized metering settlement | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.saas.finalize_metering_quota({}, content_type='application/json')
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJmaW5hbGl6ZU1ldGVyaW5nUXVvdGEifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLmdldF9ibHVlcHJpbnQiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRTYWFzQmx1ZXByaW50IiwicGF0aCI6Ii92MS9zYWFzL2JsdWVwcmludCIsInJlc291cmNlIjoic2FhcyIsInNlY3Rpb25fc2hhMjU2IjoiMDBkMTU4NGZiMDQyNzQ0MzNlM2UwZGZjYjBkZWUyMDM1MmUzYTEwMmNmMjFiN2IxYWE5YzJhNDc1OGJkM2VlNCIsInNpZ25hdHVyZV9zaGEyNTYiOiJmNGZlMDY4MmYwZTdiNGU5MGUxZmRiM2VhMWRhNjZjMTI1NjJmYzU3ZjNlZGZkNGM1YzAyOTQ2MDE1NTQxMWYwIn0 -->
### `client.saas.get_blueprint`

Operation ID: `getSaasBlueprint`  
Route: `GET` `/v1/saas/blueprint`  
Equivalent member: `client.get_saas_blueprint`  

#### Signature

```python
client.saas.get_blueprint(*, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> None
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Autonomous SaaS blueprint | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.saas.get_blueprint()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRTYWFzQmx1ZXByaW50In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLmlzc3VlX3N1cmZhY2VfbGVhc2UiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiaXNzdWVTdXJmYWNlTGVhc2UiLCJwYXRoIjoiL3YxL3NhYXMvc3VyZmFjZS1sZWFzZS9pc3N1ZSIsInJlc291cmNlIjoic2FhcyIsInNlY3Rpb25fc2hhMjU2IjoiNWE4MzExNzFkYjc0MjQ1OGM5YzEyZmRhN2U0MGQyMmY4Mzg2MGQzYjFjOTJhYmRhMWQ3MTI2MTVkZjQwZjljMSIsInNpZ25hdHVyZV9zaGEyNTYiOiJmMjc0NTM0MjY5M2EyZTA3ZjM5ZTA4OTMwMjA0NGU0NzMzOTM5ZGQzZGY2ODUyNDdhOTgxNjgxYmE5YjUyYTVjIn0 -->
### `client.saas.issue_surface_lease`

Operation ID: `issueSurfaceLease`  
Route: `POST` `/v1/saas/surface-lease/issue`  
Equivalent member: `client.issue_surface_lease`  

#### Signature

```python
client.saas.issue_surface_lease(body: dict[str, Any], *, content_type: Optional[str] = None, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> None
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Issued surface lease token | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.saas.issue_surface_lease({}, content_type='application/json')
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJpc3N1ZVN1cmZhY2VMZWFzZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLnJlc2VydmVfbWV0ZXJpbmdfcXVvdGEiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicmVzZXJ2ZU1ldGVyaW5nUXVvdGEiLCJwYXRoIjoiL3YxL3NhYXMvbWV0ZXJpbmcvcmVzZXJ2ZSIsInJlc291cmNlIjoic2FhcyIsInNlY3Rpb25fc2hhMjU2IjoiOWRjMDJlNjk0ZTAyYjFkOGQ1YWNjYzdkNDgzMjU5MDc0YjI2NTAzNGI0Y2Q3MDM2ZGFlNGI5NGQ2YWJjMzU1OSIsInNpZ25hdHVyZV9zaGEyNTYiOiI3ZTdiNzI4YjJmN2QwYzg3NzA4OWYzMDhjZjc4MjYyODU0NTU2NjI5MThkNzc2NjBlNjU5OTFmZmMzNzRkOTRhIn0 -->
### `client.saas.reserve_metering_quota`

Operation ID: `reserveMeteringQuota`  
Route: `POST` `/v1/saas/metering/reserve`  
Equivalent member: `client.reserve_metering_quota`  

#### Signature

```python
client.saas.reserve_metering_quota(body: dict[str, Any], *, content_type: Optional[str] = None, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> None
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Metering reservation record | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.saas.reserve_metering_quota({}, content_type='application/json')
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZXNlcnZlTWV0ZXJpbmdRdW90YSJ9 -->

## Resource `sbom`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYm9tLmdlbmVyYXRlIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImdlbmVyYXRlU2JvbSIsInBhdGgiOiIvdjEvc2JvbSIsInJlc291cmNlIjoic2JvbSIsInNlY3Rpb25fc2hhMjU2IjoiNTliNDJiY2E1ZDAxMTZjZTBmOGI0OGNjYWNhYjI5ZmI1MDBjNDdmYjViZWE5ZjFlZDg4MTYwYmJmY2I0ZmY5ZCIsInNpZ25hdHVyZV9zaGEyNTYiOiI5OTQ3ZDY5ZWNlMDVlNDViOTgwMWM0NGI0ZjdmNDFmZTlhYmFjY2VmZTIzNzA5NGIzOTg1ODIwYjJiODBhM2NiIn0 -->
### `client.sbom.generate`

Operation ID: `generateSbom`  
Route: `POST` `/v1/sbom`  
Equivalent member: `client.generate_sbom`  

#### Signature

```python
client.sbom.generate(body: ReviewRequest, *, content_type: Optional[str] = None, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> None
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | CycloneDX 1.5 SBOM JSON | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.sbom.generate({'files': [{'filename': 'example'}]}, content_type='application/json')
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZW5lcmF0ZVNib20ifQ -->

## Resource `supply_chain`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzdXBwbHlfY2hhaW4uYW5hbHl6ZSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJhbmFseXplU3VwcGx5Q2hhaW4iLCJwYXRoIjoiL3YxL3N1cHBseS1jaGFpbi9hbmFseXplIiwicmVzb3VyY2UiOiJzdXBwbHlfY2hhaW4iLCJzZWN0aW9uX3NoYTI1NiI6IjQ5NTJkNGQ4YjIyZmFkZDdmYTJlODFkOTRiMDRhZTBkNjg3ZGY3MzNjNTRkM2QxNjIwNzk4MDA3ODUzNGQ3MDQiLCJzaWduYXR1cmVfc2hhMjU2IjoiNmI0MjQwNjUwZWRmZjFiMTAxOWY4OGEwNTUzYTE5MjVlZDA5OTFjODFiN2FmMzdjZjI4MGQyYzZmMDg3MTU2ZCJ9 -->
### `client.supply_chain.analyze`

Operation ID: `analyzeSupplyChain`  
Route: `POST` `/v1/supply-chain/analyze`  
Equivalent member: `client.analyze_supply_chain`  

#### Signature

```python
client.supply_chain.analyze(body: ReviewRequest, *, content_type: Optional[str] = None, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> None
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Supply-chain security audit | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.supply_chain.analyze({'files': [{'filename': 'example'}]}, content_type='application/json')
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJhbmFseXplU3VwcGx5Q2hhaW4ifQ -->

## Resource `tasks`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ0YXNrcy5jcmVhdGVfY29kaW5nIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImNyZWF0ZUNvZGluZ1Rhc2siLCJwYXRoIjoiL3YxL3Rhc2tzIiwicmVzb3VyY2UiOiJ0YXNrcyIsInNlY3Rpb25fc2hhMjU2IjoiZDFiOThlODE2NTBmZDZmZjkyZDFkZmQ3ZGQyNDMyMzQwMGFjZGM2ZWYzZGYyY2Y5NDViMDc3NGFlMmYxZmYxZiIsInNpZ25hdHVyZV9zaGEyNTYiOiI2NDE2YjhiNzhkNjU0NDM0NTIyZDhlYzYzZmMxNWNkMGYyOGJhNzhiMDVhOTg1N2ViOGQzZTBhN2NiNzNhOTJmIn0 -->
### `client.tasks.create_coding`

Operation ID: `createCodingTask`  
Route: `POST` `/v1/tasks`  
Equivalent member: `client.create_coding_task`  

#### Signature

```python
client.tasks.create_coding(body: dict[str, Any], *, content_type: Optional[str] = None, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> None
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Created coding task | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.tasks.create_coding({}, content_type='application/json')
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVDb2RpbmdUYXNrIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ0YXNrcy5saXN0X2NvZGluZyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6Imxpc3RDb2RpbmdUYXNrcyIsInBhdGgiOiIvdjEvdGFza3MiLCJyZXNvdXJjZSI6InRhc2tzIiwic2VjdGlvbl9zaGEyNTYiOiJhNTg3ZmVjZWI3MWQ3ZjJmMTQxMDM3ODQzNGEzMzgwODRiYTA1ZTU4ZTNlNTQ2YWY4MjgwNGMwZTc2OTNjYjlhIiwic2lnbmF0dXJlX3NoYTI1NiI6ImJkOTBmZTc1ZDc4ZGI2ZDQzMzE0ZDIzMGI2NWQ4NGUxZjE3OTUyODdhOGYzMGYzN2YxYTg5NzQ5N2IwYWRhMDEifQ -->
### `client.tasks.list_coding`

Operation ID: `listCodingTasks`  
Route: `GET` `/v1/tasks`  
Equivalent member: `client.list_coding_tasks`  

#### Signature

```python
client.tasks.list_coding(*, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> None
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Task list | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.tasks.list_coding()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0Q29kaW5nVGFza3MifQ -->

## Resource `triage`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ0cmlhZ2UuZ2V0X3F1ZXVlIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0VHJpYWdlUXVldWUiLCJwYXRoIjoiL3YxL3RyaWFnZSIsInJlc291cmNlIjoidHJpYWdlIiwic2VjdGlvbl9zaGEyNTYiOiI1OTk4YjEyMDg0ZTFlYzM0MDhiOGY3MzAzNzFlZmE3ZTkyODY0Y2U1NGE4N2Y0ODZhNjY2Y2UyMTJlZDE5ZTM0Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjQxOTNiYTdhNWRhMTY1ZjEwN2U4OTY4NGNlYWIwNjc0ZDYxNzdlNWQzYTg2OGJmYzQyYmUxY2Y3NzdlY2MwZWEifQ -->
### `client.triage.get_queue`

Operation ID: `getTriageQueue`  
Route: `GET` `/v1/triage`  
Equivalent member: `client.get_triage_queue`  

#### Signature

```python
client.triage.get_queue(*, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> None
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Triaged PR queue | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.triage.get_queue()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRUcmlhZ2VRdWV1ZSJ9 -->

## Resource `waitlist`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3YWl0bGlzdC5saXN0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdFdhaXRsaXN0IiwicGF0aCI6Ii92MS93YWl0bGlzdCIsInJlc291cmNlIjoid2FpdGxpc3QiLCJzZWN0aW9uX3NoYTI1NiI6IjJmNGJjMGQxOGRkMjkxOTEwNDM0NTZlOWFmNzRlNWU5M2Q5MWE2M2Y5NTI4ODc0MDRkZGI3MDI1ZjY2YWY0YmQiLCJzaWduYXR1cmVfc2hhMjU2IjoiMGFhMDFiZGE1ZTBkNGQ2YmMzNDdlZjlmZGFlMTZkNGI0YWE5ZTlmZmQ2NjNmNDdlMTRkOGQ2MmZlODA1MjVkZiJ9 -->
### `client.waitlist.list`

Operation ID: `listWaitlist`  
Route: `GET` `/v1/waitlist`  
Equivalent member: `client.list_waitlist`  

#### Signature

```python
client.waitlist.list(*, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> None
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Waitlist entries | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.waitlist.list()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0V2FpdGxpc3QifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3YWl0bGlzdC5yZWdpc3RlciIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJyZWdpc3RlcldhaXRsaXN0IiwicGF0aCI6Ii92MS93YWl0bGlzdCIsInJlc291cmNlIjoid2FpdGxpc3QiLCJzZWN0aW9uX3NoYTI1NiI6IjA2YmJmYTc3MjdmMTNjNTkwYWQ1MDM3MzQ2ZjMyNWFiNTVmNDMyMTRlMjlkNzJjZGIxNjI1YjQ2MjI5ZWU1NDciLCJzaWduYXR1cmVfc2hhMjU2IjoiZjMyNGQ3NThmZjdkZWNmNDdiYzEzNmYwZjZlMDAxMjQ1NThlNjUyNDRkYmViZGM2Y2IwZTExOWQ3ZGM0YjkxOSJ9 -->
### `client.waitlist.register`

Operation ID: `registerWaitlist`  
Route: `POST` `/v1/waitlist`  
Equivalent member: `client.register_waitlist`  

#### Signature

```python
client.waitlist.register(body: WaitlistRequest, *, content_type: Optional[str] = None, headers: Optional[Mapping[str, str]] = None, query: Optional[Mapping[str, Any]] = None, cookies: Optional[Mapping[str, str]] = None, timeout: Optional[float] = None, max_retries: Optional[int] = None, max_response_bytes: Optional[int] = None, idempotency_key: Optional[str] = None) -> None
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `WaitlistRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Waitlist entry created | none |

#### Canonical required-input example

```json
{
  "body": {
    "email": "example-c65f@example.test"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```python
result = client.waitlist.register({'email': 'example-c65f@example.test'}, content_type='application/json')
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZWdpc3RlcldhaXRsaXN0In0 -->

