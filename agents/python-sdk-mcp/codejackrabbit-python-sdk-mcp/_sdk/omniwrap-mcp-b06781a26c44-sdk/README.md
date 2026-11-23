# omniwrap-mcp-b06781a26c44-sdk

Executable synchronous and asynchronous `httpx` SDK generated from `CodeJackRabbit`.
It supports injected transports, OpenAPI path/query/header/cookie serialization, JSON,
form, multipart, text and binary bodies, API-key/Basic/Bearer authentication, timeouts,
idempotent retries and structured `APIError` responses. Recognized `error.code`
or flat `code` values raise exact contract-derived subclasses before
declared HTTP statuses are considered; unknown code/status combinations retain
`APIError`. Nonstandard declared statuses export `HTTP<status>Error`; declared
4XX/5XX ranges cover their respective error statuses, while default alone does not
invent a status. `body` retains the parsed payload (None on decoding failure), and
`raw_body` retains the buffered bytes without reading the stream again. Sync and
async clients export and raise the same classes. TypeScript/JavaScript currently
retain generic status/normalized-code fallbacks, so this is not cross-language
dispatch parity. The historical `ApiError` import remains an alias of `APIError`. Every
request carries `User-Agent: omniwrap-mcp-b06781a26c44-sdk/0.3.4 python-httpx/<version>`.

```python
from omniwrap_mcp_b06781a26c44_sdk import Client, AsyncClient
```

The client defaults to `https://api.codejackrabbit.com`; pass `base_url` to target another
deployment:

```python
client = Client(base_url="https://api.codejackrabbit.com")
```

Flat methods are exposed under deterministic PEP 8 `lower_snake_case`
identifiers. The complete mapping is also stored in `omniwrap-artifact.json`
under `surface.operation_methods`; renamed entries are:

| operationId | Python method |
| --- | --- |
| `collectDeveloperAudit` | `client.collect_developer_audit()` |
| `currentDeveloperIdentity` | `client.current_developer_identity()` |
| `submitDeveloperEvidence` | `client.submit_developer_evidence()` |
| `providerCostEvidence` | `client.provider_cost_evidence()` |
| `managedAuditSnapshots` | `client.managed_audit_snapshots()` |
| `declareDeveloperProjectContext` | `client.declare_developer_project_context()` |
| `getHealth` | `client.get_health()` |
| `getCapabilities` | `client.get_capabilities()` |
| `listWaitlist` | `client.list_waitlist()` |
| `registerWaitlist` | `client.register_waitlist()` |
| `createReview` | `client.create_review()` |
| `buildAutofixBundle` | `client.build_autofix_bundle()` |
| `computeRiskRadar` | `client.compute_risk_radar()` |
| `analyzeSupplyChain` | `client.analyze_supply_chain()` |
| `generateSbom` | `client.generate_sbom()` |
| `getAnalyticsRoi` | `client.get_analytics_roi()` |
| `analyzeContractDrift` | `client.analyze_contract_drift()` |
| `exportSarif` | `client.export_sarif()` |
| `evaluateComplianceGate` | `client.evaluate_compliance_gate()` |
| `planStackedPrSplit` | `client.plan_stacked_pr_split()` |
| `analyzePerfFinOps` | `client.analyze_perf_fin_ops()` |
| `getTriageQueue` | `client.get_triage_queue()` |
| `listCodingTasks` | `client.list_coding_tasks()` |
| `createCodingTask` | `client.create_coding_task()` |
| `getSaasBlueprint` | `client.get_saas_blueprint()` |
| `issueSurfaceLease` | `client.issue_surface_lease()` |
| `reserveMeteringQuota` | `client.reserve_metering_quota()` |
| `finalizeMeteringQuota` | `client.finalize_metering_quota()` |


Operations are grouped into resource accessors derived from the contract's tags or
path segments, so calls read as `client.<resource>.<method>()`:

<!-- omniwrap-resource-example:python -->
```python
from omniwrap_mcp_b06781a26c44_sdk import Client


def run_resource_example(client: Client):
    return client.developer_intelligence.collect_audit({'from': '2026-01-09', 'repositoryId': '1', 'to': '2026-01-18'}, content_type='application/json')
```

Every resource method exists on both `Client` and `AsyncClient`.


Every decoded response keeps the exact wire payload: an omitted member stays omitted. `field_value(payload, name)` returns the `UNSET` sentinel for an absent member, `None` only for an explicit null, and `field_presence(payload, name)` names the three states directly (`absent`, `null`, `value`). Members the contract does not declare are never dropped; `unknown_fields(model, payload)` returns them and `retain_unknown_fields(model, payload)` collects them under `__omniwrap_unknown__`, with `MODEL_FIELDS` holding each model's declared wire members.

`client.with_raw_response.<operation>()` and `await async_client.with_raw_response.<operation>()` take the same arguments as the plain call and return `RawResponse`, whose `data` is the decoded value on first access (also available through `parse()`). `content` gives the exact bounded bytes without typed decoding; malformed JSON remains readable until `data` or `parse()` is requested. `status_code`, `headers` and `request_id` describe the transport. `request_id` reads the same `x-request-id`/`request-id` header an `APIError` reports, and page results carry it as `page.request_id`. Streaming operations and operations that select a response protocol at call time have no raw accessor.

For operations whose success bodies are exclusively declared as `string` with `format: binary` under concrete declared media types, `client.with_streaming_response.<operation>()` and `await async_client.with_streaming_response.<operation>()` return `BinaryResponse` and `AsyncBinaryResponse` after headers, before reading the full body. They expose `status_code`, `headers`, and `request_id`. `read(size)` returns up to 1?65536 available bytes; `iter_bytes(chunk_size)` yields bounded chunks (use `async for` on AsyncClient). The cumulative decoded body is bounded by `max_response_bytes`, including unread bytes received in a transport chunk. The response owns the connection: use `with response` or `async with response`, or explicitly call `close()` or `await aclose()`. Exhaustion, read failure, overflow and cancellation also close it. Close a partially consumed iterator explicitly when retaining it after an early exit. No typed decoding or full-body `content` property is supplied on this surface. Plain binary calls remain buffered; their `stream_response=True` selector remains unsupported. JSON, mixed representations and unproven binary schemas have no binary stream accessor.

`api_key` feeds the contract's security scheme whatever its type when exactly one scheme is declared. When every operation requires authentication, constructing a client without `api_key`, `access_token`, or `auth` raises `MissingCredentialsError` -- an `AuthenticationError` with no `status_code`, because no request was ever sent. Every credential may also be a zero-argument callable that returns the current secret; it is invoked per request.

## Per-scheme credentials

This contract declares several security schemes, so `Client` and `AsyncClient` take one keyword argument per scheme. A scheme reads, in order: `auth["<Scheme>"]`, its argument, the generic argument bound to it, its environment variable, then its declared fallback scheme. A generic argument feeds only the scheme listed beside it; no other scheme reuses a credential unless a fallback is declared, and a missing credential raises `MissingCredentialsError` naming the operation, the scheme and what to set.

| Scheme | Argument | Generic argument | Environment variable | Fallback |
|---|---|---|---|---|
| `apiKeyHeader` | `api_key_header` | `api_key` | none | none |
| `bearerAuth` | `bearer` | none | none | none |
| `managedSession` | `managed_session` | none | none | none |

## Errors

Every exception the SDK raises derives from `OmniwrapMcpB06781a26c44Error`, so one `except` covers
the whole surface. `APIError` (and its status/code subclasses) carries `status_code`,
`headers`, `body`, `raw_body`, `code`, `request_id`, `operation_id`, `attempts` and `retryable`;
its message quotes the server's own `error.message` / `message` / `detail` / `title`
when the body has one. A recognized `error.code` selects the more precise class
before declared HTTP statuses: only exact contract-declared codes are recognized.
Unknown code/status combinations retain `APIError`. `APIResponseValidationError`
reports a successful response whose body is not the JSON the contract promised.
`InvalidArgumentError` (a `TypeError`) rejects a call before any request is sent,
`ConfigurationError` (a `ValueError`) rejects an unusable client configuration,
and `ApiConnectionError` / `ApiTimeoutError` report transport failures after the
retry budget. The server's own verdict wins: `x-should-retry: true` or `false`
overrides the status policy (408, 409, 429 and 5xx), and its wait is honoured from
`retry-after-ms`, then `Retry-After` (seconds or HTTP-date), then an IETF
`RateLimit` reset (`t=` or `RateLimit-Reset`); otherwise waits back off
exponentially with jitter. A server asking for longer than `max_retry_delay`
(default 60 s) gets its error surfaced at once, and `retry_budget` caps a whole
call. `fallback_base_urls` lists ordered alternates to `base_url`, used only by
idempotent operations after a connection failure or a 5xx. Inject `sleep` and
`random` to make retries deterministic in tests.

SDK transport, HTTP, argument and credential errors carry `remediation`, a JSON-serializable
`Remediation` dict an agent or a log pipeline can act on: a stable `code`
(`authentication_failed`, `not_found`, `rate_limited`, `validation_failed`,
`missing_argument`, `timeout`, ...), the `cause` (the server's RFC 9457
`detail` when it sends one), a suggested `action`, `retryable` and `docs`.
Where they apply it names the SDK `parameter` and JSON `pointer` at fault, the
security `schemes` and `credential_options` of a refused credential, the
server-directed `retry_after` in seconds and per-field `fields` errors.
Configured credential values are redacted from it.

`error.remediation["recovery"]` adds the versioned `omniwrap.sdk-recovery/v1`
observation. `before_effects` means local validation/authentication refused the
call; `acknowledged` means a successful HTTP response was received but decoding
failed; `in_doubt` means a mutation may already have taken effect. Reconcile
uncertain mutations before replay. HTTP status, an inferred idempotence hint,
or a model suggestion cannot make them safe to retry. Only a read-only operation
may have `retry_safe: true`; still apply bounded retries and server wait guidance.
The binding includes operation, contract fingerprint, source/package versions
and a deterministic projection digest, which is not an archive hash or signature.
Export only this recovery object for Studio's local SDK delivery inspector.
Ordinary Python signature-binding `TypeError` and user hook errors can occur
before generated handling and carry no recovery record. Automatic transport
retry and authentication options retain their existing behavior.

Method signatures use `snake_case` argument names mapped to the wire names
(`pet_id` -> `petId`, `x_trace_id` -> `X-Trace-Id`); required arguments are
positional, optional parameters and transport options are keyword-only, and every
method carries a docstring derived from the contract.

## Hooks and tracing

`Client(hooks=Hooks(...))` and `AsyncClient(hooks=Hooks(...))` observe every
call. Each attempt starts with `before_request` and ends with exactly one of
`on_retry` (another attempt follows), `after_response` (the success the call
returns) or `on_error` (the failure it raises): a call that succeeds after one
retried 503 reports `before_request`, `on_retry`, `before_request`,
`after_response`, and a connection failure that is not retried reports
`before_request`, `on_error`. Each hook receives a frozen `HookContext` with
`operation_id`, `method`, `url`, `headers`, `attempt` (from 1), `elapsed_ms`
since the call started, `status` once the server answered, `error` when the
attempt failed and `retry_delay` (seconds) on `on_retry`. Each connection of a
stream is one call, and `after_response` fires once the stream is open.

The context is read-only: no hook can change the request. It never carries a
credential: `Authorization`, `Proxy-Authorization`, `Cookie`, every API-key
header and every API-key query parameter read `[redacted]`, in `headers` and
in `url`, and so does a configured credential value found anywhere else.
`AsyncClient` awaits a hook that returns an awaitable. A hook's own exception
reaches the caller and is never retried.

`tracer` opens one span per call without any tracing dependency: the client
calls `tracer.start_span(operation_id, attributes)` with `http.request.method`
before the first attempt and `span.end(attributes)` when the call settles, with
`http.request.resend_count` (the retries) and, when the server answered,
`http.response.status_code`. `Tracer` and `TracerSpan` are the protocols it
expects. With `opentelemetry-api` installed, this adapter maps it onto
OpenTelemetry:

```python
from opentelemetry import trace

from omniwrap_mcp_b06781a26c44_sdk import Client, Hooks


class OpenTelemetryTracer:
    def __init__(self, tracer):
        self._tracer = tracer

    def start_span(self, name, attributes):
        span = self._tracer.start_span(name, attributes=dict(attributes))

        class _Span:
            def end(self, attributes):
                span.set_attributes(dict(attributes))
                span.end()

        return _Span()


client = Client(
    tracer=OpenTelemetryTracer(trace.get_tracer("my-service")),
    hooks=Hooks(on_retry=lambda context: print(context.operation_id, context.attempt, context.status)),
)
```

## Packaging

The wheel installs `api.md` and `omniwrap-artifact.json` under
`<prefix>/share/omniwrap/omniwrap_mcp_b06781a26c44_sdk/`, so SDKs installed side by side never
overwrite each other's files. On Windows without long paths enabled
(`LongPathsEnabled`), build the wheel from a project path of at most 117
characters, because the in-tree build writes
`build/bdist.win-amd64/wheel/omniwrap_mcp_b06781a26c44_sdk-0.3.4.data/data/share/omniwrap/omniwrap_mcp_b06781a26c44_sdk/omniwrap-artifact.json`
below it.

Current limitations: WebSocket transport, webhook signature verification, OAuth token
acquisition, mutual-TLS setup and custom pagination remain future conformance work.
