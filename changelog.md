## 0.5.0 - 2026-02-06
* feat: add job initialization endpoint and enhance job creation API
* Adds a new job initialization endpoint that provides intelligent suggestions for validators, enrichments, and date ranges based on query analysis. Also enhances the job creation API with additional parameters for better control over job configuration.
* Key changes:
* Add new `initialize` endpoint for pre-job query analysis and suggestions
* Enhance `create_job` API with start_date, end_date, validators, and enrichments parameters
* Add pagination support to user jobs listing endpoint
* Add new data types: ValidatorSchema, EnrichmentSchema, InitializeResponseDto
* Expose HTTP response status_code property alongside existing headers
* Update dependency versions (packaging, CLI tools)
* Expand documentation with comprehensive examples and parameter details
* Add Python 3.13-3.15 compatibility declarations
* 🌿 Generated with Fern

