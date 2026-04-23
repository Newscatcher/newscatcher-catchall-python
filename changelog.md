## 1.5.0 - 2026-04-23
### Added
* **`JobsClient.delete_job()`** — soft-deletes a job by ID; the job is flagged as deleted and no longer appears in list results (sync and async).
* **`MonitorsClient.delete_monitor()`** and **`MonitorsClient.get_monitor_status_history()`** — soft-delete a monitor or retrieve its full execution history (sync and async).
* **`search` and `ownership` optional parameters** — added to `get_user_jobs()`, `list_monitors()`, and `list_datasets()` to filter results by text substring or ownership scope (`all`, `own`, `shared`).
* **`SharingInfo` and `SharingInfoPermission` types** — new types surfacing sharing metadata; optional `sharing_info` field added to `MonitorListItemDto`, `PullJobResponseDto`, and `UserJob`.
* **`UnauthorizedError`** — new error class raised on HTTP `401` responses when credentials are missing or invalid; also exports new DTO types `DeleteJobResponseDto`, `DeleteMonitorResponseDto`, `MonitorStatusHistoryResponseDto`, `MonitorStatusEntry`, `MonitorStatusEntryStatus`, and `OwnershipFilter`.

