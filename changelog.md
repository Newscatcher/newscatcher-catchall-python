## 1.2.0 - 2026-03-16
* The SDK now provides better error handling for malformed server responses. When the server returns data that doesn't match the expected schema, a new `ParsingError` exception is raised instead of the raw Pydantic validation error, providing additional context like HTTP status code and response headers.

