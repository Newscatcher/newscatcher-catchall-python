## 1.2.0 - 2026-03-16
* The SDK now raises a specific `ParsingError` exception when server responses don't match expected schemas, providing better error context including status codes, headers, and response body. This replaces generic exceptions with more actionable error information for debugging.

