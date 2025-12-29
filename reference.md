# Reference
## Jobs
<details><summary><code>client.jobs.<a href="src/newscatcher_catchall/jobs/client.py">create_job</a>(...) -> AsyncHttpResponse[SubmitResponseBody]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Submit a natural language query to create a new processing job.
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

client = CatchAllApi(
    api_key="YOUR_API_KEY",
)
client.jobs.create_job(
    query="AI company acquisitions",
    context="Focus on deal size and acquiring company details",
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

**schema:** `typing.Optional[Schema]` 
    
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

<details><summary><code>client.jobs.<a href="src/newscatcher_catchall/jobs/client.py">get_job_status</a>(...) -> AsyncHttpResponse[StatusResponseDto]</code></summary>
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

client = CatchAllApi(
    api_key="YOUR_API_KEY",
)
client.jobs.get_job_status(
    job_id="af7a26d6-cf0b-458c-a6ed-4b6318c74da3",
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

**job_id:** `str` — Unique job identifier returned from the `/catchAll/submit` endpoint.
    
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

<details><summary><code>client.jobs.<a href="src/newscatcher_catchall/jobs/client.py">get_user_jobs</a>() -> AsyncHttpResponse[typing.List[ListUserJobsResponseDto]]</code></summary>
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

client = CatchAllApi(
    api_key="YOUR_API_KEY",
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

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.jobs.<a href="src/newscatcher_catchall/jobs/client.py">get_job_results</a>(...) -> AsyncHttpResponse[PullJobResponseDto]</code></summary>
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

client = CatchAllApi(
    api_key="YOUR_API_KEY",
)
client.jobs.get_job_results(
    job_id="af7a26d6-cf0b-458c-a6ed-4b6318c74da3",
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

**job_id:** `str` — Unique job identifier returned from the `/catchAll/submit` endpoint.
    
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
<details><summary><code>client.monitors.<a href="src/newscatcher_catchall/monitors/client.py">create_monitor</a>(...) -> AsyncHttpResponse[CreateMonitorResponseDto]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Create a monitor that runs jobs based on a reference job with a specified schedule.

**Schedule requirements:**
- Minimum 24-hour interval between executions
- Natural language format (e.g., "every day at 12 PM UTC", "every 48 hours")

**Validation:**
- Schedules below minimum frequency return error with descriptive message.
- Invalid job IDs return 400 Bad Request.
- Duplicate monitors (same job already monitored) return error.
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

client = CatchAllApi(
    api_key="YOUR_API_KEY",
)
client.monitors.create_monitor(
    reference_job_id="reference_job_id",
    schedule="every day at 12 PM UTC",
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

**reference_job_id:** `str` — Job ID to use as template for scheduled runs.
    
</dd>
</dl>

<dl>
<dd>

**schedule:** `str` 

Natural language schedule (e.g. 'every day at 12 AM EST').

**Minimum frequency:** Monitors must be scheduled at least 24 hours apart.
    
</dd>
</dl>

<dl>
<dd>

**webhook:** `typing.Optional[WebhookDto]` — Optional webhook to receive notifications when jobs complete.
    
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

<details><summary><code>client.monitors.<a href="src/newscatcher_catchall/monitors/client.py">list_monitor_jobs</a>(...) -> AsyncHttpResponse[ListMonitorJobsResponse]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns all jobs associated with a monitor, sorted by start_date.
Each job includes job_id, start_date, and end_date.
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

client = CatchAllApi(
    api_key="YOUR_API_KEY",
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

<details><summary><code>client.monitors.<a href="src/newscatcher_catchall/monitors/client.py">pull_monitor_results</a>(...) -> AsyncHttpResponse[PullMonitorResponseDto]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Retrieve aggregated results from all jobs executed by this monitor.
Includes monitor configuration, execution history, and all records collected.
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

client = CatchAllApi(
    api_key="YOUR_API_KEY",
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

<details><summary><code>client.monitors.<a href="src/newscatcher_catchall/monitors/client.py">disable_monitor</a>(...) -> AsyncHttpResponse[DisableMonitorResponse]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Disables a monitor to stop executing scheduled jobs.
Validates that the provided API key is associated with the monitor.
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

client = CatchAllApi(
    api_key="YOUR_API_KEY",
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

<details><summary><code>client.monitors.<a href="src/newscatcher_catchall/monitors/client.py">enable_monitor</a>(...) -> AsyncHttpResponse[EnableMonitorResponse]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Enables a monitor to resume executing scheduled jobs.
Validates that the provided API key is associated with the monitor.
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

client = CatchAllApi(
    api_key="YOUR_API_KEY",
)
client.monitors.enable_monitor(
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

<details><summary><code>client.monitors.<a href="src/newscatcher_catchall/monitors/client.py">list_monitors</a>() -> AsyncHttpResponse[ListMonitorsResponseDto]</code></summary>
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

client = CatchAllApi(
    api_key="YOUR_API_KEY",
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

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## Meta
<details><summary><code>client.meta.<a href="src/newscatcher_catchall/meta/client.py">health_check</a>() -> AsyncHttpResponse[HealthCheckResponse]</code></summary>
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

client = CatchAllApi(
    api_key="YOUR_API_KEY",
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

<details><summary><code>client.meta.<a href="src/newscatcher_catchall/meta/client.py">get_version</a>() -> AsyncHttpResponse[GetVersionResponse]</code></summary>
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

client = CatchAllApi(
    api_key="YOUR_API_KEY",
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

