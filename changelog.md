## 3.0.0 - 2026-05-27
### Breaking Changes
* **`MonitorsClient.create_monitor()` and `MonitorsClient.update_monitor()`** — the `webhook` parameter (type `WebhookDto`) has been replaced by `webhook_ids` (type `list[str]`); rename the argument and pass a list of webhook ID strings instead of a `WebhookDto` object.
* **`JobsClient.submit()` and `JobsClient.initialize()`** — same `webhook` → `webhook_ids` rename applies; update all callers to pass a list of webhook ID strings.
### Added
* **`client.webhooks` (`WebhooksClient` / `AsyncWebhooksClient`)** — new client for full webhook lifecycle management: `list_webhooks()`, `create_webhook()`, `get_webhook()`, `update_webhook()`, `delete_webhook()`, `test_webhook()`, `assign_webhook_resource()`, `remove_webhook_resource()`, `list_webhook_resources()`, `list_webhooks_for_resource()`, and `get_webhook_delivery_history()` (sync and async).
* **`client.projects` (`ProjectsClient` / `AsyncProjectsClient`)** — new client for project lifecycle management: `list_projects()`, `create_project()`, `get_project()`, `update_project()`, `delete_project()`, `get_project_overview()`, `list_project_resources()`, `add_resource_to_project()`, and `remove_resource_from_project()` (sync and async).
* **`JobsClient.validate_query()`** — new method (sync and async) that checks whether a query is well-formed before job submission, returning a `ValidateQueryResponseDto` with a status level, issues, and suggestions.
* **`project_id` and `webhook_ids` optional parameters** — added to `get_user_jobs()`, `list_monitors()`, `list_datasets()`, `submit()`, `initialize()`, and `create_monitor()` to filter or assign resources to a project and attach webhook notifications.
* See full changelog for all changes

## 2.0.0 - 2026-05-19
### Breaking Changes
* **`DatasetsClient.list_entities_in_dataset()`** — now issues a POST to `.../entities/list` instead of a GET to `.../entities`; filter parameters are sent as a JSON body instead of query parameters, and optional filter params now default to `OMIT` (omitted entirely) instead of `None`; remove any `None` arguments and update any code that inspects raw HTTP requests.
* **`DatasetsClient.add_entities_to_dataset()`** and **`DatasetsClient.remove_entities_from_dataset()`** — HTTP verbs were swapped and are now corrected: `add_entities_to_dataset()` issues POST and `remove_entities_from_dataset()` issues DELETE; callers who worked around the previous bug must revert their workarounds.
### Added
* **`JobsClient.submit()` / `submit_job()` `ed_score_min` parameter** — new optional integer parameter that sets a minimum relevance score threshold for connected entities in Company Watchlist jobs; records where no entity meets the threshold are excluded.
* **`create_monitor()` `timezone` parameter** — new optional IANA timezone identifier used as a fallback when the `schedule` string does not include an explicit timezone.
* **`ConnectedEntity.type` and `ConnectedEntity.company`** — new fields on `ConnectedEntity`; `type` is a required string identifying the entity type and `company` is an optional `CompanyAttributes` object with stored entity attributes.
* **`max_retries` constructor parameter** — new optional `max_retries: int = 2` parameter on `CatchAllApi`, `AsyncCatchAllApi`, `BaseClientWrapper`, `SyncClientWrapper`, and `AsyncClientWrapper` to configure the default maximum number of retries for failed requests; per-request `max_retries` in `RequestOptions` still takes precedence.
### Changed
* **`pydantic-core` dependency** — upper bound widened from `<2.44.0` to `<3.0.0`, allowing installation alongside newer pydantic-core releases.
* **`create_dataset_csv()` documentation** — updated to reflect that both `name` and `domain` columns are required in the uploaded CSV (previously only `name` was documented as required).

## 1.5.1 - 2026-04-30
* fix: improve SSE line-ending normalization and incremental decoding
* Refactor the SSE event-source parser to correctly handle all line-ending
* variants (CRLF, bare CR, LF) as required by the SSE specification, and
* switch to an incremental codec decoder so that multi-byte characters
* split across chunk boundaries are reassembled correctly. Also tighten
* the urllib3 dependency to require >=2.6.3.
* Key changes:
* Add `_normalize_sse_line_endings()` to canonicalize `\r\n` and bare `\r` to `\n` per the SSE spec
* Replace one-shot `chunk.decode()` with `codecs.getincrementaldecoder` in both `iter_sse()` and `aiter_sse()` to handle multi-byte characters split across HTTP chunks
* Flush the incremental decoder at end-of-stream and process any remaining buffered data, preventing dropped final events
* Remove the `cast(AsyncGenerator, aiter_lines())` workaround in `aiter_sse()` in favour of raw byte iteration with the new decoder
* Narrow urllib3 dependency from `>=1.26.19,<2.0.0 || >=2.2.2,<3.0.0` to `>=2.6.3,<3.0.0`
* 🌿 Generated with Fern

## 1.5.0 - 2026-04-23
### Added
* **`JobsClient.delete_job()`** — soft-deletes a job by ID; the job is flagged as deleted and no longer appears in list results (sync and async).
* **`MonitorsClient.delete_monitor()`** and **`MonitorsClient.get_monitor_status_history()`** — soft-delete a monitor or retrieve its full execution history (sync and async).
* **`search` and `ownership` optional parameters** — added to `get_user_jobs()`, `list_monitors()`, and `list_datasets()` to filter results by text substring or ownership scope (`all`, `own`, `shared`).
* **`SharingInfo` and `SharingInfoPermission` types** — new types surfacing sharing metadata; optional `sharing_info` field added to `MonitorListItemDto`, `PullJobResponseDto`, and `UserJob`.
* **`UnauthorizedError`** — new error class raised on HTTP `401` responses when credentials are missing or invalid; also exports new DTO types `DeleteJobResponseDto`, `DeleteMonitorResponseDto`, `MonitorStatusHistoryResponseDto`, `MonitorStatusEntry`, `MonitorStatusEntryStatus`, and `OwnershipFilter`.

