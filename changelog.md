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

