## 1.1.0 - 2026-02-23
* feat: add configurable logging support to SDK
* This update introduces comprehensive logging capabilities to the SDK, allowing developers to monitor HTTP requests and responses with configurable log levels and custom logger implementations.
* Key changes:
* Add new logging module with Logger, ConsoleLogger, and LogConfig classes
* Update client constructors to accept optional logging configuration parameter
* Integrate request/response logging in HTTP client with header redaction for security
* Add logging imports and exports to core module for public API access
* 🌿 Generated with Fern

