# CodeJackRabbit Python API

<!-- omniwrap-api-reference eyJjb250cmFjdF9maW5nZXJwcmludCI6ImZlMGYyMjU1OGZiNDM0MTEwODJkZjVlMDc2MmEyM2U5ZWFmOTBhOWM3MTNmZTRlZTljZmQyNzM3OTIyMjgwM2QiLCJvcGVyYXRpb25fY291bnQiOjIyLCJyZW5kZXJlciI6InB5dGhvbiIsInZlcnNpb24iOiIxLjQuMCJ9 -->

This generated index is tied to Semantic IR `1.14.0` and contract fingerprint `fe0f22558fb43411082df5e0762a23e9eaf90a9c713fe4ee9cfd27379222803d`. Every operation below is rendered from the same semantic contract and artifact-attested public member allocation as the SDK.

SDK maturity: **experimental**  
Artifact evidence: [`omniwrap-artifact.json`](omniwrap-artifact.json) binds this file by SHA-256 and is revalidated by the package gate.

## Client hooks and tracing

`Client(hooks=Hooks(...))` registers four callbacks. Every attempt starts with `before_request` and ends with exactly one of `on_retry` (another attempt follows), `after_response` (the success the call returns) or `on_error` (the failure the call reports). Each receives the operation id, the HTTP method, the URL, the request headers, the attempt number (from 1), the time elapsed since the call started and, once the server answered, the HTTP status. No context carries a credential: `Authorization`, `Proxy-Authorization`, `Cookie`, every API-key header and API-key query parameter, and any configured credential value read `[redacted]`. Every context is a frozen `HookContext`: no hook can change the request.

`Client(tracer=...)` opens one span per call through the tracer interface this SDK defines, named after the operation id, with `http.request.method`, `http.response.status_code` and `http.request.resend_count`. It needs no tracing library; README.md maps it onto the OpenTelemetry API.

## Shared types

- `ComplianceGateRequest`
- `FileChange`
- `ReviewRequest`
- `WaitlistRequest`

## Resource `analysis`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXNpcy5hbmFseXplX2NvbnRyYWN0X2RyaWZ0IiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImFuYWx5emVDb250cmFjdERyaWZ0IiwicGF0aCI6Ii92MS9hbmFseXNpcy9jb250cmFjdC1kcmlmdCIsInJlc291cmNlIjoiYW5hbHlzaXMiLCJzZWN0aW9uX3NoYTI1NiI6IjJjNDM3NzgzZTI0NThjNDU1YTk2Zjk5YzBhNWZlOTMwYmVkZGM2OGZkYjU3ZWFhOTQyNjI2ODljYmE5YzNlZjkiLCJzaWduYXR1cmVfc2hhMjU2IjoiNWI0NDljMzBkOTAwMWYyNDYzZTc5ZmM4NGNkOTZjNzAwOGZjYWFhN2FjZjllMGNhNzE2OGQzNTJkNjEwMzgzZiJ9 -->
### `client.analysis.analyze_contract_drift`

Operation ID: `analyzeContractDrift`  
Route: `POST` `/v1/analysis/contract-drift`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXNpcy5hbmFseXplX3BlcmZfZmluX29wcyIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJhbmFseXplUGVyZkZpbk9wcyIsInBhdGgiOiIvdjEvYW5hbHlzaXMvcGVyZi1maW5vcHMiLCJyZXNvdXJjZSI6ImFuYWx5c2lzIiwic2VjdGlvbl9zaGEyNTYiOiI2YzkwMDFkNTE1M2M2MGE3ZGM1NzZmNDY2NTdmOGZiYjFhZjc5ZDc3NTI3NDQ2YjdkMzFjMDk1Y2Q3Mzk4OTIyIiwic2lnbmF0dXJlX3NoYTI1NiI6IjQ0MTllYTQ2MWZhMWFmYmVhNDA4NTJhYjhjZjUxOWMyMTNjODYwMTkyY2YyYjlkYzNmNzg2ZGZmMzY2M2JiZGMifQ -->
### `client.analysis.analyze_perf_fin_ops`

Operation ID: `analyzePerfFinOps`  
Route: `POST` `/v1/analysis/perf-finops`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXNpcy5wbGFuX3N0YWNrZWRfcHJfc3BsaXQiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicGxhblN0YWNrZWRQclNwbGl0IiwicGF0aCI6Ii92MS9hbmFseXNpcy9zcGxpdC1wciIsInJlc291cmNlIjoiYW5hbHlzaXMiLCJzZWN0aW9uX3NoYTI1NiI6ImE1ZjI3MGQyZTFkOWVkODQ3YWM1NGNiYjA1NWMyZTc0YzZjNjZhOTNmMThkMzg2N2NlYzJkMGU2ODdjZDI3MWMiLCJzaWduYXR1cmVfc2hhMjU2IjoiZDk4NDg2MWI1OWRlNGMyZjQyMzE5NTJkZTg5MjRjMmE5YTUyYjkyZTE3MzI1M2Y4NDhlMDg4NThiNGQyYjU5NiJ9 -->
### `client.analysis.plan_stacked_pr_split`

Operation ID: `planStackedPrSplit`  
Route: `POST` `/v1/analysis/split-pr`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXRpY3MuZ2V0X3JvaSIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEFuYWx5dGljc1JvaSIsInBhdGgiOiIvdjEvYW5hbHl0aWNzL3JvaSIsInJlc291cmNlIjoiYW5hbHl0aWNzIiwic2VjdGlvbl9zaGEyNTYiOiJkZjRiNTY1Y2EwZTQ3Y2UzZDQyZTU3NmU5MmU4ZjU3M2ZhNDI1NzM2ZjMwZWIxMTM4ZTVhN2IzY2NhNjVlYjg5Iiwic2lnbmF0dXJlX3NoYTI1NiI6ImRhMDZkNDk5Y2VmMjJhZWRlY2E5MmZlMzEzY2ZlMDZmNTNjNjQxOTEwNDhlNzc2NmMzY2ZlOWVmYmQyYmE3MTEifQ -->
### `client.analytics.get_roi`

Operation ID: `getAnalyticsRoi`  
Route: `GET` `/v1/analytics/roi`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJjYXBhYmlsaXRpZXMuZ2V0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0Q2FwYWJpbGl0aWVzIiwicGF0aCI6Ii92MS9jYXBhYmlsaXRpZXMiLCJyZXNvdXJjZSI6ImNhcGFiaWxpdGllcyIsInNlY3Rpb25fc2hhMjU2IjoiMTg3OGNkOGQzM2YxNDMxOGJkYWY2MDBhOTFhOTNlZTBiMzQ1ODJiOTZlNGU0MGIzNDNmOGNkZjQ2NDhiN2Q0ZiIsInNpZ25hdHVyZV9zaGEyNTYiOiIzMDUxM2Y5OGI2MjBmOTZmNDkyMGE0YmZiMmQ5OWZiZWQxMmNhYWM2YTc5NmFiNjY1MmU5MDFlZDZlZmQwMWEzIn0 -->
### `client.capabilities.get`

Operation ID: `getCapabilities`  
Route: `GET` `/v1/capabilities`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJjb21wbGlhbmNlLmV2YWx1YXRlX2dhdGUiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiZXZhbHVhdGVDb21wbGlhbmNlR2F0ZSIsInBhdGgiOiIvdjEvY29tcGxpYW5jZS9nYXRlIiwicmVzb3VyY2UiOiJjb21wbGlhbmNlIiwic2VjdGlvbl9zaGEyNTYiOiI0MDUzYjM5OTJiMjFjNjMzNDA3NmFkMWU5YmIyMWE1YTc3YmUzNzBlZTViYjhiN2QwYzQ5ZjNkODk3YjE0ODgxIiwic2lnbmF0dXJlX3NoYTI1NiI6IjY2YjA1NzQyODhmYjNiZjYyNDA5NWY0NDNmMGVlYTc2YzJkZjVjOTE2ZDBhMmNjY2JiZDZhMTcwYmE5MzU2NDgifQ -->
### `client.compliance.evaluate_gate`

Operation ID: `evaluateComplianceGate`  
Route: `POST` `/v1/compliance/gate`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJjb21wbGlhbmNlLmV4cG9ydF9zYXJpZiIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJleHBvcnRTYXJpZiIsInBhdGgiOiIvdjEvY29tcGxpYW5jZS9zYXJpZiIsInJlc291cmNlIjoiY29tcGxpYW5jZSIsInNlY3Rpb25fc2hhMjU2IjoiYTkwZmFjNTc4MmJjMjIzOWFlZWI2NjZlYTM1YzJkMmYwNTFkNzcwZGNkODU4NWM0NTI3MDcwNWUxZDY0ODA0NyIsInNpZ25hdHVyZV9zaGEyNTYiOiI3ODFiNmQ5NTUzNWFlYTY5MjRiOGNjMjE5YzE4ODU4OGJkM2FkOTcxNDA4MDFhOGE1MTA1M2Y5ZmY3YTJmYmJjIn0 -->
### `client.compliance.export_sarif`

Operation ID: `exportSarif`  
Route: `POST` `/v1/compliance/sarif`  

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

## Resource `health`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJoZWFsdGguZ2V0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0SGVhbHRoIiwicGF0aCI6Ii9oZWFsdGgiLCJyZXNvdXJjZSI6ImhlYWx0aCIsInNlY3Rpb25fc2hhMjU2IjoiMzRjOGYwOTRiODM2MTdlN2RhYTU3ZmYxM2I2NDljYmEzNDAzMDA0YTY4YWZjNzlmODI0NmI2OWI3NGY3MDNlNCIsInNpZ25hdHVyZV9zaGEyNTYiOiIxOWRiZmQ0MTM1N2I1ZWZlNzVhNjU5YzA5ZjNiNWU5ZjY5YWY0YzUwNDViNTJiZGM5NmRjNzNlN2QzNjkzNWM0In0 -->
### `client.health.get`

Operation ID: `getHealth`  
Route: `GET` `/health`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJyZXZpZXdzLmJ1aWxkX2F1dG9maXhfYnVuZGxlIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImJ1aWxkQXV0b2ZpeEJ1bmRsZSIsInBhdGgiOiIvdjEvcmV2aWV3cy9hdXRvZml4IiwicmVzb3VyY2UiOiJyZXZpZXdzIiwic2VjdGlvbl9zaGEyNTYiOiI3YTA1YTYzNjJlZmExZjA3OGNiMjNmYzBjMjM5YmNkNmM3Y2Q0ODI2ZDNhZGM2MTZhZjU5YjY3ZDkxNjg1MTcyIiwic2lnbmF0dXJlX3NoYTI1NiI6IjdjNTg1MzM0MjEyYmI1MDZmNzFkYjM2NGZjMjM4ODBmMWViYjQ2MjgzMGNlOGQ4YzZjYjdmM2ZmY2UzMmJiNzIifQ -->
### `client.reviews.build_autofix_bundle`

Operation ID: `buildAutofixBundle`  
Route: `POST` `/v1/reviews/autofix`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJyZXZpZXdzLmNvbXB1dGVfcmlza19yYWRhciIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJjb21wdXRlUmlza1JhZGFyIiwicGF0aCI6Ii92MS9yZXZpZXdzL3Jpc2stcmFkYXIiLCJyZXNvdXJjZSI6InJldmlld3MiLCJzZWN0aW9uX3NoYTI1NiI6IjA1MWUxNGJmMjlkOWIwMjhlZGU0MjM3NWIyNjdlMTVmMTlkZDRhNGYxOTYyNjA0NWZlYmU0ODVmYTFkYjA4NTciLCJzaWduYXR1cmVfc2hhMjU2IjoiMDAwZGEzOWJhYzE0ZTExODcwNWQ4NTJiY2U5MGJhNTY1ZThiODI1MjMzZDZmMDRhYzA0YjY0NGNlMzg3MTEyZSJ9 -->
### `client.reviews.compute_risk_radar`

Operation ID: `computeRiskRadar`  
Route: `POST` `/v1/reviews/risk-radar`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJyZXZpZXdzLmNyZWF0ZSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJjcmVhdGVSZXZpZXciLCJwYXRoIjoiL3YxL3Jldmlld3MiLCJyZXNvdXJjZSI6InJldmlld3MiLCJzZWN0aW9uX3NoYTI1NiI6ImY3NTNlZWNjOGUxZWYzNWJhZDg3NDdiNzVjOTFmMDQ4NzQ0ZjhhNDYzNzZjOWNlZDBjZTc1MmU0ZDgwNTFlYmIiLCJzaWduYXR1cmVfc2hhMjU2IjoiMDdkZjRlMWQ0NTE4MzQ0ZGE0ZjRkZDNhMDU1NDYyM2RlZTQxZDdlNDllOTI2NWQ5ODhjOTlmZjUyNDg3NWI5MiJ9 -->
### `client.reviews.create`

Operation ID: `createReview`  
Route: `POST` `/v1/reviews`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLmZpbmFsaXplX21ldGVyaW5nX3F1b3RhIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImZpbmFsaXplTWV0ZXJpbmdRdW90YSIsInBhdGgiOiIvdjEvc2Fhcy9tZXRlcmluZy9maW5hbGl6ZSIsInJlc291cmNlIjoic2FhcyIsInNlY3Rpb25fc2hhMjU2IjoiYWY1MDEzOWIxODRkMjQzOGQ0OTJlY2YwOTcyMzkxMzg3MmY3ZWI0NGZiNzFiMjBkN2IwN2ZhZjQ3MDhkYzIzZCIsInNpZ25hdHVyZV9zaGEyNTYiOiI1YjI3NGQwYzYyMTAzMDBkM2I0NzE0NWYxNGQ5NTM4MGJjYzYzMDVkN2I3OWZiZjZkMzNjMjQzYmJmZGFmYjRiIn0 -->
### `client.saas.finalize_metering_quota`

Operation ID: `finalizeMeteringQuota`  
Route: `POST` `/v1/saas/metering/finalize`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLmdldF9ibHVlcHJpbnQiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRTYWFzQmx1ZXByaW50IiwicGF0aCI6Ii92MS9zYWFzL2JsdWVwcmludCIsInJlc291cmNlIjoic2FhcyIsInNlY3Rpb25fc2hhMjU2IjoiNjQ3MDRhMTBjZjdmODUyOWRmZWUxNjkyMmRmOTc1ODVjYTgxMGJjOGZmZTk4YmJlYzJmYjZiZWY3ODU1ZmNiMSIsInNpZ25hdHVyZV9zaGEyNTYiOiJmNGZlMDY4MmYwZTdiNGU5MGUxZmRiM2VhMWRhNjZjMTI1NjJmYzU3ZjNlZGZkNGM1YzAyOTQ2MDE1NTQxMWYwIn0 -->
### `client.saas.get_blueprint`

Operation ID: `getSaasBlueprint`  
Route: `GET` `/v1/saas/blueprint`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLmlzc3VlX3N1cmZhY2VfbGVhc2UiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiaXNzdWVTdXJmYWNlTGVhc2UiLCJwYXRoIjoiL3YxL3NhYXMvc3VyZmFjZS1sZWFzZS9pc3N1ZSIsInJlc291cmNlIjoic2FhcyIsInNlY3Rpb25fc2hhMjU2IjoiMTUzYWQzNjk3MmZiNGYxNzRhOTNkOWM5MTNlMWE0YmFkNWJjZmZiZGY0ODhlMDRmMzFhZjk4MzAwMzQyNDViMyIsInNpZ25hdHVyZV9zaGEyNTYiOiJmMjc0NTM0MjY5M2EyZTA3ZjM5ZTA4OTMwMjA0NGU0NzMzOTM5ZGQzZGY2ODUyNDdhOTgxNjgxYmE5YjUyYTVjIn0 -->
### `client.saas.issue_surface_lease`

Operation ID: `issueSurfaceLease`  
Route: `POST` `/v1/saas/surface-lease/issue`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLnJlc2VydmVfbWV0ZXJpbmdfcXVvdGEiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicmVzZXJ2ZU1ldGVyaW5nUXVvdGEiLCJwYXRoIjoiL3YxL3NhYXMvbWV0ZXJpbmcvcmVzZXJ2ZSIsInJlc291cmNlIjoic2FhcyIsInNlY3Rpb25fc2hhMjU2IjoiNjE4OGY1ZDc2MWMyOTdkZmY5YzU2MDc5MzM3N2ZjMDRhMzM3MDFmOTVlYmExOTQ0NzlhNTMwNmMzNjkzNGJhNiIsInNpZ25hdHVyZV9zaGEyNTYiOiI3ZTdiNzI4YjJmN2QwYzg3NzA4OWYzMDhjZjc4MjYyODU0NTU2NjI5MThkNzc2NjBlNjU5OTFmZmMzNzRkOTRhIn0 -->
### `client.saas.reserve_metering_quota`

Operation ID: `reserveMeteringQuota`  
Route: `POST` `/v1/saas/metering/reserve`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYm9tLmdlbmVyYXRlIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImdlbmVyYXRlU2JvbSIsInBhdGgiOiIvdjEvc2JvbSIsInJlc291cmNlIjoic2JvbSIsInNlY3Rpb25fc2hhMjU2IjoiYjJhOGYxNDk4NTU5ZTE0ODI4YjYwODU3OTdiMDZkMzk1MjE0ZjIzNjU1YjBhZDQ0ZDY5NjMwMDJjY2RiOGUxZCIsInNpZ25hdHVyZV9zaGEyNTYiOiI5OTQ3ZDY5ZWNlMDVlNDViOTgwMWM0NGI0ZjdmNDFmZTlhYmFjY2VmZTIzNzA5NGIzOTg1ODIwYjJiODBhM2NiIn0 -->
### `client.sbom.generate`

Operation ID: `generateSbom`  
Route: `POST` `/v1/sbom`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzdXBwbHlfY2hhaW4uYW5hbHl6ZSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJhbmFseXplU3VwcGx5Q2hhaW4iLCJwYXRoIjoiL3YxL3N1cHBseS1jaGFpbi9hbmFseXplIiwicmVzb3VyY2UiOiJzdXBwbHlfY2hhaW4iLCJzZWN0aW9uX3NoYTI1NiI6IjJmOTIwZDMxY2Q2NDQyYmI0MmIwMmYwYTQ3MjY4ZDU3OWViNmU1MzIxNWE2MzU0OTVjZjA0NGUwNzk1YzNjODciLCJzaWduYXR1cmVfc2hhMjU2IjoiNmI0MjQwNjUwZWRmZjFiMTAxOWY4OGEwNTUzYTE5MjVlZDA5OTFjODFiN2FmMzdjZjI4MGQyYzZmMDg3MTU2ZCJ9 -->
### `client.supply_chain.analyze`

Operation ID: `analyzeSupplyChain`  
Route: `POST` `/v1/supply-chain/analyze`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ0YXNrcy5jcmVhdGVfY29kaW5nIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImNyZWF0ZUNvZGluZ1Rhc2siLCJwYXRoIjoiL3YxL3Rhc2tzIiwicmVzb3VyY2UiOiJ0YXNrcyIsInNlY3Rpb25fc2hhMjU2IjoiYWU3MTk0M2UwODVmYzhlN2M4YTI2MGY3N2M5ZmI1NWEwOWMxZGM3NzNiMzE5ZTk5Y2IxMDY5YzQwN2RiOWVlNSIsInNpZ25hdHVyZV9zaGEyNTYiOiI2NDE2YjhiNzhkNjU0NDM0NTIyZDhlYzYzZmMxNWNkMGYyOGJhNzhiMDVhOTg1N2ViOGQzZTBhN2NiNzNhOTJmIn0 -->
### `client.tasks.create_coding`

Operation ID: `createCodingTask`  
Route: `POST` `/v1/tasks`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ0YXNrcy5saXN0X2NvZGluZyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6Imxpc3RDb2RpbmdUYXNrcyIsInBhdGgiOiIvdjEvdGFza3MiLCJyZXNvdXJjZSI6InRhc2tzIiwic2VjdGlvbl9zaGEyNTYiOiI0YzA3NjA2YmU5MTQ4N2I1ZWEzOTczYWYwZTc5MjJjODQ3NmFiNmE0NzZjMmE2MzNiNDA0NWJkODBmOTg0MzA1Iiwic2lnbmF0dXJlX3NoYTI1NiI6ImJkOTBmZTc1ZDc4ZGI2ZDQzMzE0ZDIzMGI2NWQ4NGUxZjE3OTUyODdhOGYzMGYzN2YxYTg5NzQ5N2IwYWRhMDEifQ -->
### `client.tasks.list_coding`

Operation ID: `listCodingTasks`  
Route: `GET` `/v1/tasks`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ0cmlhZ2UuZ2V0X3F1ZXVlIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0VHJpYWdlUXVldWUiLCJwYXRoIjoiL3YxL3RyaWFnZSIsInJlc291cmNlIjoidHJpYWdlIiwic2VjdGlvbl9zaGEyNTYiOiI0ZmMwYTY5NDk1NmZlNjViNzczMzY4NTZjY2M3YTVjZDk2YzUwZWFkZjg5MzY4YTI1ODIwYmMzYTVhMWMzNTQ0Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjQxOTNiYTdhNWRhMTY1ZjEwN2U4OTY4NGNlYWIwNjc0ZDYxNzdlNWQzYTg2OGJmYzQyYmUxY2Y3NzdlY2MwZWEifQ -->
### `client.triage.get_queue`

Operation ID: `getTriageQueue`  
Route: `GET` `/v1/triage`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3YWl0bGlzdC5saXN0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdFdhaXRsaXN0IiwicGF0aCI6Ii92MS93YWl0bGlzdCIsInJlc291cmNlIjoid2FpdGxpc3QiLCJzZWN0aW9uX3NoYTI1NiI6IjFiMDMzZDNjZDI4OWVhYTUzNTczZTUwNmEwYjM3OWNiOWM0YTY2ZTJlYTk1ZDZiMzQwM2YxMDc3YTI2ZmM4NDciLCJzaWduYXR1cmVfc2hhMjU2IjoiMGFhMDFiZGE1ZTBkNGQ2YmMzNDdlZjlmZGFlMTZkNGI0YWE5ZTlmZmQ2NjNmNDdlMTRkOGQ2MmZlODA1MjVkZiJ9 -->
### `client.waitlist.list`

Operation ID: `listWaitlist`  
Route: `GET` `/v1/waitlist`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3YWl0bGlzdC5yZWdpc3RlciIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJyZWdpc3RlcldhaXRsaXN0IiwicGF0aCI6Ii92MS93YWl0bGlzdCIsInJlc291cmNlIjoid2FpdGxpc3QiLCJzZWN0aW9uX3NoYTI1NiI6IjI1ZWRlODhmZTk0MzExMzkwZWNiMTFhOGQwZWE2MjQ0OTUwNTg4OGRmMGQ0OWZkNjIzN2FlOGVhNjdjNmM3OGYiLCJzaWduYXR1cmVfc2hhMjU2IjoiZjMyNGQ3NThmZjdkZWNmNDdiYzEzNmYwZjZlMDAxMjQ1NThlNjUyNDRkYmViZGM2Y2IwZTExOWQ3ZGM0YjkxOSJ9 -->
### `client.waitlist.register`

Operation ID: `registerWaitlist`  
Route: `POST` `/v1/waitlist`  

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

