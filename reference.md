# Reference
## Jobs
<details><summary><code>client.jobs.<a href="src/newscatcher_catchall/jobs/client.py">get_user_jobs</a>(...) -> ListUserJobsResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns all jobs created by the authenticated user.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.jobs.get_user_jobs()

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**page:** `typing.Optional[int]` — Page number to retrieve.
    
</dd>
</dl>

<dl>
<dd>

**page_size:** `typing.Optional[int]` — Number of records per page.
    
</dd>
</dl>

<dl>
<dd>

**search:** `typing.Optional[str]` — Filter results by text (case-insensitive substring match).
    
</dd>
</dl>

<dl>
<dd>

**ownership:** `typing.Optional[OwnershipFilter]` — Filter results by ownership. Defaults to `all`.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.jobs.<a href="src/newscatcher_catchall/jobs/client.py">initialize</a>(...) -> InitializeResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Get suggested validators, enrichments, and date ranges for a query.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.jobs.initialize(
    query="Series B funding rounds for SaaS startups",
    context="Focus on funding amount and company name",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**query:** `Query` 
    
</dd>
</dl>

<dl>
<dd>

**context:** `typing.Optional[Context]` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.jobs.<a href="src/newscatcher_catchall/jobs/client.py">create_job</a>(...) -> SubmitResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Submit a query to create a new processing job.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment
import datetime

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.jobs.create_job(
    query="Series B funding rounds for SaaS startups",
    context="Focus on funding amount and company name",
    limit=10,
    start_date=datetime.datetime.fromisoformat("2026-02-18T00:00:00+00:00"),
    end_date=datetime.datetime.fromisoformat("2026-02-23T00:00:00+00:00"),
    mode="base",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**query:** `Query` 
    
</dd>
</dl>

<dl>
<dd>

**context:** `typing.Optional[Context]` 
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[Limit]` 
    
</dd>
</dl>

<dl>
<dd>

**start_date:** `typing.Optional[StartDate]` 
    
</dd>
</dl>

<dl>
<dd>

**end_date:** `typing.Optional[EndDate]` 
    
</dd>
</dl>

<dl>
<dd>

**validators:** `typing.Optional[typing.List[ValidatorSchema]]` 

Custom validators for filtering web page clusters.

If not provided, validators are generated automatically based on the query.
    
</dd>
</dl>

<dl>
<dd>

**enrichments:** `typing.Optional[typing.List[EnrichmentSchema]]` 

Custom enrichment fields for data extraction.

If not provided, enrichments are generated automatically based on the query.
    
</dd>
</dl>

<dl>
<dd>

**mode:** `typing.Optional[SubmitRequestDtoMode]` 

Job processing mode.

- `base`: Full pipeline with validation and enrichment.
- `lite`: Lightweight extraction with faster processing. Returns titles and citations only.
    
</dd>
</dl>

<dl>
<dd>

**connected_dataset_ids:** `typing.Optional[typing.List[str]]` 

Dataset IDs to connect to this job. When provided, activates Company Watchlist mode — the job returns only events relevant to companies in the connected datasets with each record including a `connected_entities` array scored per company.

The dataset must have `latest_status: ready` before the job is submitted. Submitting with a non-existent or inaccessible dataset ID returns `400`.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.jobs.<a href="src/newscatcher_catchall/jobs/client.py">get_job_status</a>(...) -> StatusResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve the current processing status of a job.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.jobs.get_job_status(
    job_id="5f0c9087-85cb-4917-b3c7-e5a5eff73a0c",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**job_id:** `str` — Unique job identifier returned from [`POST /catchAll/submit`](https://www.newscatcherapi.com/docs/web-search-api/api-reference/jobs/create-job).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.jobs.<a href="src/newscatcher_catchall/jobs/client.py">get_job_results</a>(...) -> PullJobResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve the final results for a completed job.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.jobs.get_job_results(
    job_id="5f0c9087-85cb-4917-b3c7-e5a5eff73a0c",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**job_id:** `str` — Unique job identifier returned from [`POST /catchAll/submit`](https://www.newscatcherapi.com/docs/web-search-api/api-reference/jobs/create-job).
    
</dd>
</dl>

<dl>
<dd>

**page:** `typing.Optional[int]` — Page number to retrieve.
    
</dd>
</dl>

<dl>
<dd>

**page_size:** `typing.Optional[int]` — Number of records per page.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.jobs.<a href="src/newscatcher_catchall/jobs/client.py">continue_job</a>(...) -> ContinueResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Continue an existing job to process more records beyond the initial limit.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.jobs.continue_job(
    job_id="5f0c9087-85cb-4917-b3c7-e5a5eff73a0c",
    new_limit=100,
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**job_id:** `str` — Job identifier of the completed job to continue.
    
</dd>
</dl>

<dl>
<dd>

**new_limit:** `typing.Optional[int]` — New record limit for continued processing. Must be greater than the previous limit. If not provided, defaults to the plan maximum.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.jobs.<a href="src/newscatcher_catchall/jobs/client.py">delete_job</a>(...) -> DeleteJobResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Soft-deletes a job. The job is flagged as deleted and no longer
appears in list results. The underlying data is retained.

Only the job owner can delete a job. Returns `404` if the job is not
found or does not belong to the authenticated user.

Deleting an already-deleted job returns `200`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.jobs.delete_job(
    job_id="5f0c9087-85cb-4917-b3c7-e5a5eff73a0c",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**job_id:** `str` — Unique job identifier returned from [`POST /catchAll/submit`](https://www.newscatcherapi.com/docs/web-search-api/api-reference/jobs/create-job).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Monitors
<details><summary><code>client.monitors.<a href="src/newscatcher_catchall/monitors/client.py">list_monitors</a>(...) -> ListMonitorsResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns all monitors created by the authenticated user.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.monitors.list_monitors()

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**page:** `typing.Optional[int]` — Page number to retrieve.
    
</dd>
</dl>

<dl>
<dd>

**page_size:** `typing.Optional[int]` — Number of records per page.
    
</dd>
</dl>

<dl>
<dd>

**search:** `typing.Optional[str]` — Filter results by text (case-insensitive substring match).
    
</dd>
</dl>

<dl>
<dd>

**ownership:** `typing.Optional[OwnershipFilter]` — Filter results by ownership. Defaults to `all`.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.monitors.<a href="src/newscatcher_catchall/monitors/client.py">create_monitor</a>(...) -> CreateMonitorResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Create a scheduled monitor based on a reference job.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi, WebhookDto
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.monitors.create_monitor(
    reference_job_id="5f0c9087-85cb-4917-b3c7-e5a5eff73a0c",
    schedule="every day at 12 PM UTC",
    webhook=WebhookDto(
        url="https://your-endpoint.com/webhook",
        method="POST",
        headers={
            "Authorization": "Bearer your_token_here"
        },
    ),
    limit=10,
    backfill=True,
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**reference_job_id:** `str` 

Job ID to use as template for scheduled runs. Defines the query, validators, and enrichments used for each scheduled run.

If [`backfill`](https://www.newscatcherapi.com/docs/web-search-api/api-reference/monitors/create-monitor#body-backfill) is true, the job's `end_date` must be within the last 7 days.
    
</dd>
</dl>

<dl>
<dd>

**schedule:** `str` 

Monitor schedule in plain text format (e.g. 'every day at 12 PM UTC', 'every 48 hours').

Minimum frequency depends on your plan.
    
</dd>
</dl>

<dl>
<dd>

**webhook:** `typing.Optional[WebhookDto]` — Optional webhook to receive notifications when jobs complete.
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum number of records per monitor run. If not provided, defaults to the plan limit.
    
</dd>
</dl>

<dl>
<dd>

**backfill:** `typing.Optional[bool]` 

If true, fills the data gap between the reference job's `end_date` and the first scheduled run. The reference job's `end_date` must be within the last 7 days. 

If false, no gap filling occurs and the first run uses the current cron window only — the reference job's age does not matter.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.monitors.<a href="src/newscatcher_catchall/monitors/client.py">pull_monitor_results</a>(...) -> PullMonitorResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve aggregated results from all jobs executed by a monitor.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.monitors.pull_monitor_results(
    monitor_id="monitor_id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**monitor_id:** `str` — Monitor identifier.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.monitors.<a href="src/newscatcher_catchall/monitors/client.py">list_monitor_jobs</a>(...) -> ListMonitorJobsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Return all jobs executed by a monitor.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.monitors.list_monitor_jobs(
    monitor_id="monitor_id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**monitor_id:** `str` — Monitor identifier.
    
</dd>
</dl>

<dl>
<dd>

**sort:** `typing.Optional[ListMonitorJobsRequestSort]` — Sort by start_date (asc or desc).
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.monitors.<a href="src/newscatcher_catchall/monitors/client.py">get_monitor_status_history</a>(...) -> MonitorStatusHistoryResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns the full execution history of a monitor as a list of status entries, ordered from newest to oldest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.monitors.get_monitor_status_history(
    monitor_id="monitor_id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**monitor_id:** `str` — Monitor identifier.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.monitors.<a href="src/newscatcher_catchall/monitors/client.py">enable_monitor</a>(...) -> EnableMonitorResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Resume scheduled job execution for a monitor.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.monitors.enable_monitor(
    monitor_id="monitor_id",
    backfill=True,
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**monitor_id:** `str` — Monitor identifier.
    
</dd>
</dl>

<dl>
<dd>

**backfill:** `typing.Optional[bool]` 

If true, fills the data gap between the last job's `end_date` and the first scheduled run after enabling. The last job's `end_date` must be within the last 7 days. 

If false, no gap filling occurs and the first run uses the current cron window only — the last job's age does not matter.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.monitors.<a href="src/newscatcher_catchall/monitors/client.py">disable_monitor</a>(...) -> DisableMonitorResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Stop scheduled job execution for a monitor.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.monitors.disable_monitor(
    monitor_id="monitor_id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**monitor_id:** `str` — Monitor identifier.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.monitors.<a href="src/newscatcher_catchall/monitors/client.py">delete_monitor</a>(...) -> DeleteMonitorResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Soft-deletes a monitor. The monitor is flagged as deleted, stops
executing scheduled jobs immediately, and no longer appears in list
results.

Only the monitor owner can delete a monitor. Returns `404` if the
monitor is not found or does not belong to the authenticated user.

Deleting an already-deleted monitor returns `200`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.monitors.delete_monitor(
    monitor_id="monitor_id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**monitor_id:** `str` — Monitor identifier.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.monitors.<a href="src/newscatcher_catchall/monitors/client.py">update_monitor</a>(...) -> UpdateMonitorResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Update the webhook configuration for an existing monitor.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi, WebhookDto
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.monitors.update_monitor(
    monitor_id="monitor_id",
    webhook=WebhookDto(
        url="https://new-endpoint.com/webhook",
        method="POST",
        headers={
            "Authorization": "Bearer new_token_xyz"
        },
    ),
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**monitor_id:** `str` — Monitor identifier.
    
</dd>
</dl>

<dl>
<dd>

**webhook:** `typing.Optional[WebhookDto]` — Updated webhook configuration.
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Updated maximum number of records per monitor run.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Entities
<details><summary><code>client.entities.<a href="src/newscatcher_catchall/entities/client.py">list_entities</a>(...) -> EntityListResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a paginated list of entities belonging to the authenticated
organization. Supports filtering by status and entity type, and
sorting by name, status, or creation date.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.entities.list_entities(
    search="NewsCatcher",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**page:** `typing.Optional[int]` — Page number to retrieve.
    
</dd>
</dl>

<dl>
<dd>

**page_size:** `typing.Optional[int]` — Number of entities per page.
    
</dd>
</dl>

<dl>
<dd>

**search:** `typing.Optional[str]` — Filter entities by name (case-insensitive substring match).
    
</dd>
</dl>

<dl>
<dd>

**status:** `typing.Optional[EntityStatus]` 
    
</dd>
</dl>

<dl>
<dd>

**entity_type:** `typing.Optional[EntityType]` 
    
</dd>
</dl>

<dl>
<dd>

**sort_by:** `typing.Optional[EntitySortBy]` 
    
</dd>
</dl>

<dl>
<dd>

**sort_order:** `typing.Optional[SortOrder]` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.entities.<a href="src/newscatcher_catchall/entities/client.py">create_entity</a>(...) -> CreateEntityResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates a new company entity and begins background enrichment.

The entity status starts as `pending` and transitions to `ready` once
enrichment completes. Provide as much identifying information as
possible — `domain` is the highest-signal field because it is
unambiguous.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi, AdditionalAttributes, CompanyAttributes
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.entities.create_entity(
    name="NewsCatcher",
    entity_type="company",
    description="AI-powered news data provider",
    additional_attributes=AdditionalAttributes(
        company_attributes=CompanyAttributes(
            domain="newscatcherapi.com",
            key_persons=[
                "Artem Bugara",
                "Maksym Sugonyaka"
            ],
            alternative_names=[
                "NC",
                "NewsCatcher API"
            ],
        ),
    ),
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `CreateEntityRequest` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.entities.<a href="src/newscatcher_catchall/entities/client.py">create_entities_batch</a>(...) -> CreateEntitiesBatchResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates multiple entities in a single request. Each entity is
processed independently — a failure in one does not affect others.

Returns an array of `{id, status}` objects in the same order as
the input array.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi, CreateEntityRequest, AdditionalAttributes, CompanyAttributes
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.entities.create_entities_batch(
    entities=[
        CreateEntityRequest(
            name="OpenAI",
            entity_type="company",
            description="Artificial intelligence research company",
            additional_attributes=AdditionalAttributes(
                company_attributes=CompanyAttributes(
                    domain="openai.com",
                    key_persons=[
                        "Sam Altman"
                    ],
                    alternative_names=[
                        "Open AI"
                    ],
                ),
            ),
        ),
        CreateEntityRequest(
            name="Stripe",
            entity_type="company",
            description="Online payment processing platform",
            additional_attributes=AdditionalAttributes(
                company_attributes=CompanyAttributes(
                    domain="stripe.com",
                    key_persons=[
                        "Patrick Collison",
                        "John Collison"
                    ],
                ),
            ),
        )
    ],
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entities:** `typing.List[CreateEntityRequest]` 

Array of entities to create. Each item follows the same schema
as single entity creation.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.entities.<a href="src/newscatcher_catchall/entities/client.py">get_entity</a>(...) -> EntityResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a single entity by ID with all attributes and current status.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.entities.get_entity(
    entity_id="854198fa-f702-49db-a381-0427fa87f173",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entity_id:** `str` — Unique entity identifier.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.entities.<a href="src/newscatcher_catchall/entities/client.py">delete_entity</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Permanently deletes an entity. The entity is removed from all
datasets and the search index. This operation cannot be undone.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.entities.delete_entity(
    entity_id="854198fa-f702-49db-a381-0427fa87f173",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entity_id:** `str` — Unique entity identifier.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.entities.<a href="src/newscatcher_catchall/entities/client.py">update_entity</a>(...) -> EntityResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates one or more fields of an existing entity.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi, AdditionalAttributes, CompanyAttributes
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.entities.update_entity(
    entity_id="854198fa-f702-49db-a381-0427fa87f173",
    description="Updated description",
    additional_attributes=AdditionalAttributes(
        company_attributes=CompanyAttributes(
            alternative_names=[
                "NC",
                "NewsCatcher API",
                "NCA"
            ],
        ),
    ),
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**entity_id:** `str` — Unique entity identifier.
    
</dd>
</dl>

<dl>
<dd>

**name:** `typing.Optional[str]` — Updated entity name.
    
</dd>
</dl>

<dl>
<dd>

**description:** `typing.Optional[str]` — Updated description.
    
</dd>
</dl>

<dl>
<dd>

**additional_attributes:** `typing.Optional[AdditionalAttributes]` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Datasets
<details><summary><code>client.datasets.<a href="src/newscatcher_catchall/datasets/client.py">list_datasets</a>(...) -> DatasetListResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a paginated list of datasets belonging to the authenticated
organization. Supports filtering by status and sorting by name,
status, or creation date.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.datasets.list_datasets(
    search="Portfolio",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**page:** `typing.Optional[int]` — Page number to retrieve.
    
</dd>
</dl>

<dl>
<dd>

**page_size:** `typing.Optional[int]` — Number of datasets per page.
    
</dd>
</dl>

<dl>
<dd>

**search:** `typing.Optional[str]` — Filter datasets by name (case-insensitive substring match).
    
</dd>
</dl>

<dl>
<dd>

**latest_status:** `typing.Optional[DatasetStatus]` — Filter by dataset status.
    
</dd>
</dl>

<dl>
<dd>

**sort_by:** `typing.Optional[DatasetSortBy]` 
    
</dd>
</dl>

<dl>
<dd>

**sort_order:** `typing.Optional[SortOrder]` 
    
</dd>
</dl>

<dl>
<dd>

**ownership:** `typing.Optional[OwnershipFilter]` — Filter results by ownership. Defaults to `all`.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.datasets.<a href="src/newscatcher_catchall/datasets/client.py">create_dataset</a>(...) -> DatasetResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates a new dataset from a list of existing entity IDs.

If any of the provided entity IDs do not exist or do not belong to
your organization, the request fails with `400`. All entity IDs must
be valid before the dataset is created.

To create a dataset and entities in one step, use the [`Create dataset from CSV`](https://www.newscatcherapi.com/docs/web-search-api/api-reference/datasets/create-dataset-from-csv)
endpoint instead.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.datasets.create_dataset(
    name="My Portfolio",
    description="Companies in our investment portfolio",
    entity_ids=[
        "854198fa-f702-49db-a381-0427fa87f173",
        "a1b2c3d4-e5f6-7890-abcd-ef1234567890"
    ],
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**name:** `str` — Name for the dataset.
    
</dd>
</dl>

<dl>
<dd>

**description:** `typing.Optional[str]` — Optional description.
    
</dd>
</dl>

<dl>
<dd>

**entity_ids:** `typing.Optional[typing.List[str]]` — IDs of existing entities to include in the dataset. All IDs must belong to the authenticated organization. If any ID is invalid or not found, the request fails with `400`.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.datasets.<a href="src/newscatcher_catchall/datasets/client.py">create_dataset_from_csv</a>(...) -> CreateDatasetCsvResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates a new dataset by uploading a CSV file. Each row in the CSV
becomes an entity. The `name` column is required; all other columns
are optional.

**CSV format:**
```csv
name,description,domain,alternative_names,key_persons
NewsCatcher,"AI-powered news data provider",newscatcherapi.com,"NC;NewsCatcher API","Artem Bugara;Maksym Sugonyaka"
OpenAI,"Artificial intelligence research company",openai.com,"Open AI","Sam Altman"
```

Use semicolons (`;`) to separate multiple values in `alternative_names` and `key_persons`. Rows with empty `name` are skipped and reported in `validation_report`. 

**Note**: The response shape differs from the JSON dataset creation endpoint: it returns `dataset_id` (not `id`) and includes a `validation_report` with details on skipped rows.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.datasets.create_dataset_from_csv(
    file="example_file",
    name="name",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**file:** `core.File` — The CSV file to upload.
    
</dd>
</dl>

<dl>
<dd>

**name:** `str` — Name for the new dataset.
    
</dd>
</dl>

<dl>
<dd>

**description:** `typing.Optional[str]` — Optional description for the dataset.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.datasets.<a href="src/newscatcher_catchall/datasets/client.py">get_dataset</a>(...) -> DatasetResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a single dataset by ID including entity count and current status.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.datasets.get_dataset(
    dataset_id="ccabb755-afc2-4047-b84c-78d1f23d49b2",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**dataset_id:** `str` — Unique dataset identifier.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.datasets.<a href="src/newscatcher_catchall/datasets/client.py">delete_dataset</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Permanently deletes a dataset. The entities within the dataset are
not deleted — only the dataset itself. This operation cannot be
undone.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.datasets.delete_dataset(
    dataset_id="ccabb755-afc2-4047-b84c-78d1f23d49b2",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**dataset_id:** `str` — Unique dataset identifier.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.datasets.<a href="src/newscatcher_catchall/datasets/client.py">update_dataset</a>(...) -> DatasetResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates the name or description of a dataset.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.datasets.update_dataset(
    dataset_id="ccabb755-afc2-4047-b84c-78d1f23d49b2",
    name="My Portfolio (updated)",
    description="Updated Q1 2026 watchlist",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**dataset_id:** `str` — Unique dataset identifier.
    
</dd>
</dl>

<dl>
<dd>

**name:** `typing.Optional[str]` — Updated dataset name.
    
</dd>
</dl>

<dl>
<dd>

**description:** `typing.Optional[str]` — Updated description.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.datasets.<a href="src/newscatcher_catchall/datasets/client.py">list_entities_in_dataset</a>(...) -> DatasetEntityListResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a paginated list of entities in a dataset. Supports filtering by status and entity type.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.datasets.list_entities_in_dataset(
    dataset_id="ccabb755-afc2-4047-b84c-78d1f23d49b2",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**dataset_id:** `str` — Unique dataset identifier.
    
</dd>
</dl>

<dl>
<dd>

**page:** `typing.Optional[int]` — Page number to retrieve.
    
</dd>
</dl>

<dl>
<dd>

**page_size:** `typing.Optional[int]` — Number of entities per page.
    
</dd>
</dl>

<dl>
<dd>

**search:** `typing.Optional[str]` — Filter entities by name.
    
</dd>
</dl>

<dl>
<dd>

**status:** `typing.Optional[EntityStatus]` 
    
</dd>
</dl>

<dl>
<dd>

**entity_type:** `typing.Optional[EntityType]` 
    
</dd>
</dl>

<dl>
<dd>

**sort_by:** `typing.Optional[EntitySortBy]` 
    
</dd>
</dl>

<dl>
<dd>

**sort_order:** `typing.Optional[SortOrder]` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.datasets.<a href="src/newscatcher_catchall/datasets/client.py">add_entities_to_dataset</a>(...) -> ManageEntitiesResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Adds one or more existing entities to a dataset. Returns the number of entities added.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.datasets.add_entities_to_dataset(
    dataset_id="ccabb755-afc2-4047-b84c-78d1f23d49b2",
    entity_ids=[
        "854198fa-f702-49db-a381-0427fa87f173"
    ],
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**dataset_id:** `str` — Unique dataset identifier.
    
</dd>
</dl>

<dl>
<dd>

**request:** `DatasetEntityIdsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.datasets.<a href="src/newscatcher_catchall/datasets/client.py">remove_entities_from_dataset</a>(...) -> ManageEntitiesResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Removes one or more entities from a dataset. The entities themselves
are not deleted — they are only removed from this dataset. Returns
the number of entities removed.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.datasets.remove_entities_from_dataset(
    dataset_id="ccabb755-afc2-4047-b84c-78d1f23d49b2",
    entity_ids=[
        "854198fa-f702-49db-a381-0427fa87f173"
    ],
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**dataset_id:** `str` — Unique dataset identifier.
    
</dd>
</dl>

<dl>
<dd>

**request:** `DatasetEntityIdsRequest` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.datasets.<a href="src/newscatcher_catchall/datasets/client.py">get_dataset_status_history</a>(...) -> DatasetStatusHistoryResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns the full status change history for a dataset, ordered
chronologically from oldest to newest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.datasets.get_dataset_status_history(
    dataset_id="ccabb755-afc2-4047-b84c-78d1f23d49b2",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**dataset_id:** `str` — Unique dataset identifier.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.datasets.<a href="src/newscatcher_catchall/datasets/client.py">upload_csv_to_dataset</a>(...) -> UploadCsvToDatasetResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Appends new companies to an existing dataset by uploading a CSV file.
Uses the same CSV format as the dataset creation endpoint.

The response omits `dataset_name` compared to the create-from-CSV
endpoint since the dataset already exists.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.datasets.upload_csv_to_dataset(
    dataset_id="ccabb755-afc2-4047-b84c-78d1f23d49b2",
    file="example_file",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**dataset_id:** `str` — Unique dataset identifier.
    
</dd>
</dl>

<dl>
<dd>

**file:** `core.File` — The CSV file to upload.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Meta
<details><summary><code>client.meta.<a href="src/newscatcher_catchall/meta/client.py">health_check</a>() -> HealthCheckResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Check API availability.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.meta.health_check()

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.meta.<a href="src/newscatcher_catchall/meta/client.py">get_version</a>() -> GetVersionResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns current API version.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.meta.get_version()

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.meta.<a href="src/newscatcher_catchall/meta/client.py">get_plan_limits</a>() -> GetPlanLimitsResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns plan features and current usage for the authenticated organization.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.meta.get_plan_limits()

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

