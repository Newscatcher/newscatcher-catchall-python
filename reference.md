# Reference
## Jobs
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

## Monitors
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

