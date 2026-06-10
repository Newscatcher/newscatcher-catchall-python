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

client.jobs.get_user_jobs(
    project_id="60a85db4-78ec-4b78-876a-bc7d9cdadd04",
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

**ownership:** `typing.Optional[OwnershipFilter]` 
    
</dd>
</dl>

<dl>
<dd>

**project_id:** `typing.Optional[str]` — Filter results to resources belonging to this project.
    
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

<details><summary><code>client.jobs.<a href="src/newscatcher_catchall/jobs/client.py">validate_query</a>(...) -> ValidateQueryResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Checks whether a query is well-formed and likely to produce good results before submitting a job.

Returns a quality assessment with a status level, identified issues, and actionable suggestions.
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

client.jobs.validate_query(
    query="Series B funding rounds for SaaS startups",
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

**query:** `str` — Plain text query to validate.
    
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

**connected_dataset_ids:** `typing.Optional[typing.List[str]]` — Optional list of watchlist dataset IDs connected to this job.
    
</dd>
</dl>

<dl>
<dd>

**fetch_all_watchlist_news:** `typing.Optional[bool]` 

When true, returns generic news validators and enrichments suitable for
watchlist-based article collection instead of query-specific fields.
    
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

Dataset IDs to connect to the job. When provided, this enables Company Watchlist mode — the job returns only events relevant to companies in the connected datasets. To set the minimum relevance threshold, use `ed_score_min`.

The dataset must have `latest_status: ready` before the job is submitted. Submitting with a non-existent or inaccessible dataset ID returns `400`.
    
</dd>
</dl>

<dl>
<dd>

**ed_score_min:** `typing.Optional[int]` 

The minimum relevance score a connected entity must reach for its record to be included in results.

Only valid when `connected_dataset_ids` is set; otherwise ignored. Records where no connected entity meets the threshold are excluded entirely.
    
</dd>
</dl>

<dl>
<dd>

**project_id:** `typing.Optional[str]` — Project to assign this job to. The job appears in the project's resource list immediately after submission.
    
</dd>
</dl>

<dl>
<dd>

**webhook_ids:** `typing.Optional[typing.List[str]]` — IDs of webhooks to notify when the job completes. Maximum 5 per job.
    
</dd>
</dl>

<dl>
<dd>

**fetch_all_watchlist_news:** `typing.Optional[bool]` 

When true, retrieves all news for connected Company Watchlist entities
without topic filtering. Requires connected_dataset_ids to be set.
    
</dd>
</dl>

<dl>
<dd>

**ed_association_type:** `typing.Optional[EntityAssociationType]` 

Filter events by entity association type. `event_associated` keeps only
events where the entity is a direct actor. `mention` keeps only events
where the entity is merely referenced. Only relevant when
connected_dataset_ids is set.
    
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

Soft-deletes a job. The job is flagged as deleted and no longer appears in list results. The underlying data is retained.

Only the job owner can delete a job. Returns `404` if the job is not found or does not belong to the authenticated user.

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

client.monitors.list_monitors(
    project_id="60a85db4-78ec-4b78-876a-bc7d9cdadd04",
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

**ownership:** `typing.Optional[OwnershipFilter]` 
    
</dd>
</dl>

<dl>
<dd>

**project_id:** `typing.Optional[str]` — Filter results to resources belonging to this project.
    
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
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.monitors.create_monitor(
    reference_job_id="5f0c9087-85cb-4917-b3c7-e5a5eff73a0c",
    schedule="every day at 12 PM",
    timezone="UTC",
    webhook_ids=[
        "a1b2c3d4-e5f6-7890-abcd-ef1234567890"
    ],
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

**schedule:** `str` — Monitor schedule in plain text format. Minimum frequency depends on your plan.
    
</dd>
</dl>

<dl>
<dd>

**timezone:** `typing.Optional[str]` 

The IANA timezone identifier used as the fallback when the `schedule` string does not include an explicit timezone.

If the schedule includes a timezone abbreviation (for example, `"every day at 9am EST"`), the parsed timezone takes priority and this value is ignored. 
    
</dd>
</dl>

<dl>
<dd>

**webhook_ids:** `typing.Optional[typing.List[str]]` 

IDs of centralized webhooks to notify on each run completion.
Passing IDs here is equivalent to calling
`POST /catchAll/webhooks/{webhook_id}/resources` for each ID after creation.
Maximum 5 per monitor.
    
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

**project_id:** `typing.Optional[str]` — Project to assign this monitor to. The monitor appears in the project's resource list after creation.
    
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
from newscatcher_catchall import CatchAllApi
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.monitors.update_monitor(
    monitor_id="monitor_id",
    webhook_ids=[
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

**monitor_id:** `str` — Monitor identifier.
    
</dd>
</dl>

<dl>
<dd>

**webhook_ids:** `typing.Optional[typing.List[str]]` 

Updated list of centralized webhook IDs for this monitor. 

Replaces all existing webhook assignments. Pass an empty array `[]` to clear all assignments. Omit to leave existing assignments unchanged.
    
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

## Webhooks
<details><summary><code>client.webhooks.<a href="src/newscatcher_catchall/webhooks/client.py">list_webhooks</a>(...) -> ListWebhooksResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a paginated list of webhooks belonging to the organization.
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

client.webhooks.list_webhooks()

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

**page_size:** `typing.Optional[int]` — Number of webhooks per page.
    
</dd>
</dl>

<dl>
<dd>

**search:** `typing.Optional[str]` — Filter results by text (case-insensitive substring match).
    
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

<details><summary><code>client.webhooks.<a href="src/newscatcher_catchall/webhooks/client.py">create_webhook</a>(...) -> CreateWebhookResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates a new webhook endpoint for the organization.
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

client.webhooks.create_webhook(
    name="Layoffs Alert",
    url="https://hooks.slack.com/services/T000/B000/xxx",
    type="slack",
    delivery_mode="full",
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

**name:** `str` — Human-readable label for this webhook.
    
</dd>
</dl>

<dl>
<dd>

**url:** `str` 

Destination URL that receives the payload. Must use HTTPS. IP addresses are not accepted.

Type-specific URL requirements:
- `slack`: Must start with `https://hooks.slack.com/`.
- `teams`: Hostname must match `*.webhook.office.com` or `*.webhook.office365.com`.
- `generic`: Any valid HTTPS domain.
- `custom`: Any valid HTTPS domain.

When `type` is omitted, it is auto-detected from the URL.
    
</dd>
</dl>

<dl>
<dd>

**type:** `typing.Optional[WebhookType]` 
    
</dd>
</dl>

<dl>
<dd>

**delivery_mode:** `typing.Optional[DeliveryMode]` 
    
</dd>
</dl>

<dl>
<dd>

**method:** `typing.Optional[HttpMethod]` 
    
</dd>
</dl>

<dl>
<dd>

**headers:** `typing.Optional[typing.Dict[str, str]]` — Custom HTTP headers forwarded with each delivery.
    
</dd>
</dl>

<dl>
<dd>

**params:** `typing.Optional[typing.Dict[str, str]]` — Query parameters appended to the webhook URL.
    
</dd>
</dl>

<dl>
<dd>

**auth:** `typing.Optional[CreateWebhookRequestDtoAuth]` 

Authentication forwarded with each delivery. Supported types:
- `bearer`: Adds an `Authorization: Bearer <token>` header.
- `api_key`: Adds a custom header with the specified name and value.
- `basic`: Adds an `Authorization: Basic <credentials>` header.
    
</dd>
</dl>

<dl>
<dd>

**formatter_config:** `typing.Optional[typing.Dict[str, typing.Any]]` — Custom payload transformation configuration. Required only when `type` is `custom`.
    
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

<details><summary><code>client.webhooks.<a href="src/newscatcher_catchall/webhooks/client.py">get_webhook</a>(...) -> GetWebhookResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns the full configuration of a single webhook by ID.
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

client.webhooks.get_webhook(
    webhook_id="a1b2c3d4-e5f6-7890-abcd-ef1234567890",
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

**webhook_id:** `str` — Unique webhook identifier.
    
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

<details><summary><code>client.webhooks.<a href="src/newscatcher_catchall/webhooks/client.py">delete_webhook</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Permanently deletes a webhook and removes all resource assignments. 

Assigned jobs and monitors no longer trigger delivery to this webhook. This operation cannot be undone.
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

client.webhooks.delete_webhook(
    webhook_id="a1b2c3d4-e5f6-7890-abcd-ef1234567890",
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

**webhook_id:** `str` — Unique webhook identifier.
    
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

<details><summary><code>client.webhooks.<a href="src/newscatcher_catchall/webhooks/client.py">update_webhook</a>(...) -> UpdateWebhookResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates one or more fields of an existing webhook.
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

client.webhooks.update_webhook(
    webhook_id="a1b2c3d4-e5f6-7890-abcd-ef1234567890",
    name="Layoffs Alert (EU)",
    is_active=False,
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

**webhook_id:** `str` — Unique webhook identifier.
    
</dd>
</dl>

<dl>
<dd>

**name:** `typing.Optional[str]` — Updated webhook name.
    
</dd>
</dl>

<dl>
<dd>

**url:** `typing.Optional[str]` — Updated destination URL. Must use HTTPS. Type-specific URL rules apply.
    
</dd>
</dl>

<dl>
<dd>

**type:** `typing.Optional[WebhookType]` 
    
</dd>
</dl>

<dl>
<dd>

**delivery_mode:** `typing.Optional[DeliveryMode]` 
    
</dd>
</dl>

<dl>
<dd>

**method:** `typing.Optional[HttpMethod]` 
    
</dd>
</dl>

<dl>
<dd>

**headers:** `typing.Optional[typing.Dict[str, str]]` — Updated HTTP headers. Replaces existing headers entirely.
    
</dd>
</dl>

<dl>
<dd>

**params:** `typing.Optional[typing.Dict[str, str]]` — Updated query parameters. Replaces existing params entirely.
    
</dd>
</dl>

<dl>
<dd>

**auth:** `typing.Optional[UpdateWebhookRequestDtoAuth]` — Updated authentication configuration. Replaces existing auth entirely.
    
</dd>
</dl>

<dl>
<dd>

**formatter_config:** `typing.Optional[typing.Dict[str, typing.Any]]` — Updated formatter configuration.
    
</dd>
</dl>

<dl>
<dd>

**is_active:** `typing.Optional[bool]` — Set to `false` to disable delivery without deleting the webhook.
    
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

<details><summary><code>client.webhooks.<a href="src/newscatcher_catchall/webhooks/client.py">test_webhook</a>(...) -> TestWebhookResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Sends a test HTTP request to the webhook URL using the webhook's configured method, headers, and auth. Returns the response from the target endpoint.

Use this to verify URL reachability and authentication before attaching the webhook to a live job or monitor.
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

client.webhooks.test_webhook(
    webhook_id="a1b2c3d4-e5f6-7890-abcd-ef1234567890",
    payload={
        "test": True,
        "message": "CatchAll webhook test"
    },
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

**webhook_id:** `str` — Unique webhook identifier.
    
</dd>
</dl>

<dl>
<dd>

**payload:** `typing.Optional[typing.Dict[str, typing.Any]]` 

Custom payload to send in the test request. If omitted, a synthetic
test payload is sent.
    
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

<details><summary><code>client.webhooks.<a href="src/newscatcher_catchall/webhooks/client.py">list_webhook_resources</a>(...) -> ListWebhookResourcesResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a paginated list of resources currently assigned to this webhook.
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

client.webhooks.list_webhook_resources(
    webhook_id="a1b2c3d4-e5f6-7890-abcd-ef1234567890",
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

**webhook_id:** `str` — Unique webhook identifier.
    
</dd>
</dl>

<dl>
<dd>

**resource_type:** `typing.Optional[MappableResourceType]` 
    
</dd>
</dl>

<dl>
<dd>

**page:** `typing.Optional[int]` — Page number to retrieve.
    
</dd>
</dl>

<dl>
<dd>

**page_size:** `typing.Optional[int]` — Number of assignments per page.
    
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

<details><summary><code>client.webhooks.<a href="src/newscatcher_catchall/webhooks/client.py">assign_webhook_resource</a>(...) -> AssignWebhookResourceResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Attaches a job, monitor, or monitor group to the webhook. When the
resource completes, the webhook receives a delivery.

A single webhook can be assigned to multiple resources. Each resource
can have up to 5 webhooks assigned.
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

client.webhooks.assign_webhook_resource(
    webhook_id="a1b2c3d4-e5f6-7890-abcd-ef1234567890",
    resource_type="monitor",
    resource_id="3fec5b07-8786-46d7-9486-d43ff67eccd4",
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

**webhook_id:** `str` — Unique webhook identifier.
    
</dd>
</dl>

<dl>
<dd>

**resource_type:** `MappableResourceType` — Type of resource to assign.
    
</dd>
</dl>

<dl>
<dd>

**resource_id:** `str` — ID of the resource to assign.
    
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

<details><summary><code>client.webhooks.<a href="src/newscatcher_catchall/webhooks/client.py">remove_webhook_resource</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Detaches a resource from this webhook. Completions of the resource no longer trigger delivery to this webhook.

The webhook and the resource itself are not deleted.
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

client.webhooks.remove_webhook_resource(
    webhook_id="a1b2c3d4-e5f6-7890-abcd-ef1234567890",
    resource_type="job",
    resource_id="3fec5b07-8786-46d7-9486-d43ff67eccd4",
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

**webhook_id:** `str` — Unique webhook identifier.
    
</dd>
</dl>

<dl>
<dd>

**resource_type:** `MappableResourceType` 
    
</dd>
</dl>

<dl>
<dd>

**resource_id:** `str` — Unique resource identifier.
    
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

<details><summary><code>client.webhooks.<a href="src/newscatcher_catchall/webhooks/client.py">list_webhooks_for_resource</a>(...) -> ListWebhooksResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns all webhooks currently assigned to the given resource.
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

client.webhooks.list_webhooks_for_resource(
    resource_type="job",
    resource_id="3fec5b07-8786-46d7-9486-d43ff67eccd4",
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

**resource_type:** `MappableResourceType` 
    
</dd>
</dl>

<dl>
<dd>

**resource_id:** `str` — Unique resource identifier.
    
</dd>
</dl>

<dl>
<dd>

**is_active:** `typing.Optional[bool]` — Filter by active status. Omit to return webhooks regardless of status.
    
</dd>
</dl>

<dl>
<dd>

**page:** `typing.Optional[int]` — Page number to retrieve.
    
</dd>
</dl>

<dl>
<dd>

**page_size:** `typing.Optional[int]` — Number of webhooks per page.
    
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

<details><summary><code>client.webhooks.<a href="src/newscatcher_catchall/webhooks/client.py">get_webhook_delivery_history</a>(...) -> DeliveryHistoryResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a paginated delivery log for a given resource, ordered by timestamp descending. 

Each record shows the webhook dispatched, the HTTP status code returned, delivery outcome, and any error or warning messages. Use this to debug failed deliveries or audit dispatch activity.
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

client.webhooks.get_webhook_delivery_history(
    resource_type="job",
    resource_id="3fec5b07-8786-46d7-9486-d43ff67eccd4",
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

**resource_type:** `MappableResourceType` — Type of the resource to retrieve delivery history for.
    
</dd>
</dl>

<dl>
<dd>

**resource_id:** `str` — Identifier of the resource to retrieve delivery history for.
    
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

## Entities
<details><summary><code>client.entities.<a href="src/newscatcher_catchall/entities/client.py">list_entities</a>(...) -> EntityListResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a paginated list of entities belonging to the authenticated organization. Supports filtering by status and entity type, and sorting by name, status, or creation date.
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

Creates multiple entities in a single request. Each entity is processed independently — a failure in one does not affect others.

Returns an array of `{id, status}` objects in the same order as the input array.
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

Returns a paginated list of datasets belonging to the authenticated organization. Supports filtering by status and sorting by name, status, or creation date.
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
    project_id="60a85db4-78ec-4b78-876a-bc7d9cdadd04",
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

**ownership:** `typing.Optional[OwnershipFilter]` 
    
</dd>
</dl>

<dl>
<dd>

**project_id:** `typing.Optional[str]` — Filter results to resources belonging to this project.
    
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

Creates a new dataset by uploading a CSV file. Each row in the CSV becomes an entity. The `name` and `domain`columns are required; all other columns are optional.

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

Removes one or more entities from a dataset. The entities themselves are not deleted — they are only removed from this dataset. Returns the number of entities removed.
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

<details><summary><code>client.datasets.<a href="src/newscatcher_catchall/datasets/client.py">list_entities_in_dataset</a>(...) -> DatasetEntityListResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a paginated list of entities in a dataset. Supports filtering by status, entity type, and name search.
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
    page=1,
    page_size=100,
    search="OpenAI",
    status="ready",
    entity_type="company",
    sort_by="created_at",
    sort_order="desc",
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

**page:** `typing.Optional[int]` — The page number to retrieve.
    
</dd>
</dl>

<dl>
<dd>

**page_size:** `typing.Optional[int]` — The number of entities per page.
    
</dd>
</dl>

<dl>
<dd>

**search:** `typing.Optional[str]` — Filters entities by name using a case-insensitive substring match.
    
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

<details><summary><code>client.datasets.<a href="src/newscatcher_catchall/datasets/client.py">get_dataset_status_history</a>(...) -> DatasetStatusHistoryResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns the full status change history for a dataset, ordered chronologically from oldest to newest.
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

Appends new companies to an existing dataset by uploading a CSV file. Uses the same CSV format as the dataset creation endpoint.

The response omits `dataset_name` compared to the create-from-CSV endpoint since the dataset already exists.
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

## Projects
<details><summary><code>client.projects.<a href="src/newscatcher_catchall/projects/client.py">list_projects</a>(...) -> ProjectListResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns all projects visible to the authenticated user.
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

client.projects.list_projects(
    search="M&A",
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

**page_size:** `typing.Optional[int]` — Number of records per page.
    
</dd>
</dl>

<dl>
<dd>

**search:** `typing.Optional[str]` — Filter by project name (case-insensitive substring match).
    
</dd>
</dl>

<dl>
<dd>

**ownership:** `typing.Optional[OwnershipFilter]` 
    
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

<details><summary><code>client.projects.<a href="src/newscatcher_catchall/projects/client.py">create_project</a>(...) -> CreateProjectResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates a new project.
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

client.projects.create_project(
    name="AI M&A Tracking",
    description="Tracks AI-related M&A activity for our investment team.",
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

**name:** `str` — Name for the project.
    
</dd>
</dl>

<dl>
<dd>

**description:** `typing.Optional[str]` — Optional description.
    
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

<details><summary><code>client.projects.<a href="src/newscatcher_catchall/projects/client.py">get_project</a>(...) -> ProjectResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a single project by ID.
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

client.projects.get_project(
    project_id="60a85db4-78ec-4b78-876a-bc7d9cdadd04",
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

**project_id:** `str` — Unique project identifier.
    
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

<details><summary><code>client.projects.<a href="src/newscatcher_catchall/projects/client.py">delete_project</a>(...)</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Deletes a project. By default, assigned resources are unassigned but not deleted. 
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

client.projects.delete_project(
    project_id="60a85db4-78ec-4b78-876a-bc7d9cdadd04",
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

**project_id:** `str` — Unique project identifier.
    
</dd>
</dl>

<dl>
<dd>

**delete_resources:** `typing.Optional[bool]` — If true, permanently deletes all resources (jobs, monitors, datasets) assigned to the project. If false, the project is deleted and its resources are unassigned but not deleted.
    
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

<details><summary><code>client.projects.<a href="src/newscatcher_catchall/projects/client.py">update_project</a>(...) -> UpdateProjectResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Updates the name or description of an existing project.
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

client.projects.update_project(
    project_id="60a85db4-78ec-4b78-876a-bc7d9cdadd04",
    name="AI M&A Tracking (Q2 2026)",
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

**project_id:** `str` — Unique project identifier.
    
</dd>
</dl>

<dl>
<dd>

**name:** `typing.Optional[str]` — New name for the project.
    
</dd>
</dl>

<dl>
<dd>

**description:** `typing.Optional[str]` — New description for the project.
    
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

<details><summary><code>client.projects.<a href="src/newscatcher_catchall/projects/client.py">get_project_overview</a>(...) -> ProjectOverviewResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns resource counts for a project, grouped by type and status.

For `jobs` and `monitors`, counts are broken down by status (for example, `completed`, `failed`). For `datasets` and `monitor_groups`, only a `total` count is returned.
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

client.projects.get_project_overview(
    project_id="60a85db4-78ec-4b78-876a-bc7d9cdadd04",
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

**project_id:** `str` — Unique project identifier.
    
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

<details><summary><code>client.projects.<a href="src/newscatcher_catchall/projects/client.py">list_project_resources</a>(...) -> ProjectResourceListResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns all resources assigned to a project, with optional filtering by type.
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

client.projects.list_project_resources(
    project_id="60a85db4-78ec-4b78-876a-bc7d9cdadd04",
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

**project_id:** `str` — Unique project identifier.
    
</dd>
</dl>

<dl>
<dd>

**resource_type:** `typing.Optional[ProjectResourceType]` 
    
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

<details><summary><code>client.projects.<a href="src/newscatcher_catchall/projects/client.py">add_resource_to_project</a>(...) -> AddResourceResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Assigns one or more existing resources to a project in a single request.
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
from newscatcher_catchall import CatchAllApi, ResourceItemDto
from newscatcher_catchall.environment import CatchAllApiEnvironment

client = CatchAllApi(
    api_key="<value>",
    environment=CatchAllApiEnvironment.DEFAULT,
)

client.projects.add_resource_to_project(
    project_id="60a85db4-78ec-4b78-876a-bc7d9cdadd04",
    resources=[
        ResourceItemDto(
            resource_type="job",
            resource_id="48421e16-1f50-4048-b62c-d3bc0789d30d",
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

**project_id:** `str` — Unique project identifier.
    
</dd>
</dl>

<dl>
<dd>

**resources:** `typing.List[ResourceItemDto]` — Resources to assign to the project.
    
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

<details><summary><code>client.projects.<a href="src/newscatcher_catchall/projects/client.py">remove_resource_from_project</a>(...) -> RemoveResourceResponseDto</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Removes a resource from a project. The resource itself is not
deleted — it becomes unassigned and continues to exist.
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

client.projects.remove_resource_from_project(
    project_id="60a85db4-78ec-4b78-876a-bc7d9cdadd04",
    resource_type="job",
    resource_id="48421e16-1f50-4048-b62c-d3bc0789d30d",
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

**project_id:** `str` — Unique project identifier.
    
</dd>
</dl>

<dl>
<dd>

**resource_type:** `ProjectResourceType` 
    
</dd>
</dl>

<dl>
<dd>

**resource_id:** `str` — ID of the resource to remove.
    
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

