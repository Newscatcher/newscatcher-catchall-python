# NewsCatcher CatchAll Python SDK

Python library for NewsCatcher CatchAll API

## Installation

```bash
pip install newscatcher-catchall-sdk
```

## Usage

```python
from newscatcher_catchall import CatchAllApi

client = CatchAllApi(api_key="YOUR_API_KEY")

# Create a job
response = client.create_job(
    query="Tech company earnings this quarter"
)
```

## Documentation

For detailed documentation, visit [NewsCatcher CatchAll API Documentation](https://www.newscatcherapi.com/docs/v3/catch-all/overview/introduction)
