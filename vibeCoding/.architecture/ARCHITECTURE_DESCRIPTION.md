# ARCHITECTURE DESCRIPTION

The response must provide one or more architectural component, adhering to this format and describes the solution.


# PROBLEM STATEMENT

## Objective

- System:
  - We want to design a cloud-native, document-conversion application.
- Users / actors:
  - Browser-based users on the web accessing a website to convert files to different formats
- Primary outcome:
  - Allows a host of conversion for different common filestypes

## Scope boundaries

- In scope:
  - Common text files formats such as docx, docs, markdown, raw text, PDF, rst...
  - Common geo files such as gpx, kml, kmz, geojson
- Out of scope:
  - Videos, photos, audio and media files

## Assumptions

- The application will live in the cloud
- users with upload their files via a web browser
- they will get their files back via file download after the conversion is finished

## Architectural components

### 10 — Web Conversion Experience

- Category:
  - client
- Purpose:
  - Provide a browser interface where users upload files, choose output formats, and retrieve conversion results.
- Responsibilities:
  - Collect file upload and conversion options
  - Display conversion job status and result availability
  - Provide secure file download flow for completed results
  - Surface user-facing errors and guidance
- Interfaces:
  - Incoming:
    - User actions (file selection, format choice, convert request, download request)
  - Outgoing:
    - Conversion submission requests
    - Job status polling or subscription requests
    - Result retrieval requests
- Data / state:
  - Transient UI state for selected files and requested output format
  - Session-scoped references to submitted job identifiers
- Interactions:
  - User-facing:
    - Upload form, progress/status display, download action
  - Internal synchronous:
    - Calls to API and access control boundaries for upload token, job creation, and result access
  - Internal asynchronous:
    - Optional status update events delivered to the browser session
- Security / access considerations:
  - Must avoid exposing internal storage locations
  - Must ensure only authorized sessions can access upload/download operations
- Observability / operational considerations:
  - Capture client-visible failure types and conversion completion latency metrics
- Dependencies:
  - 20, 30
- Constraints / notes:
  - Must support large-file UX constraints such as upload progress and retry guidance

### 20 — Conversion Control API

- Category:
  - orchestration
- Purpose:
  - Provide the system boundary for conversion operations and coordinate request validation, job lifecycle, and response shaping.
- Responsibilities:
  - Validate incoming conversion requests against supported scope
  - Create and manage conversion jobs through lifecycle states
  - Route conversion work to processing components and track completion
  - Expose status and retrieval metadata for completed jobs
- Interfaces:
  - Incoming:
    - Conversion job creation requests
    - Job status requests
    - Result retrieval requests
  - Outgoing:
    - Job dispatch commands to conversion processing
    - Job state updates to lifecycle persistence
    - Access-scoped retrieval instructions for output artifacts
- Data / state:
  - Job metadata, requested source and target formats, lifecycle state, timestamps, and failure reasons
- Interactions:
  - User-facing:
    - None directly; exposed via web client and API contract
  - Internal synchronous:
    - Validation and metadata persistence interactions
  - Internal asynchronous:
    - Dispatch and completion signals for conversion processing
- Security / access considerations:
  - Enforce request-level authorization and ownership checks for job and result access
  - Apply input constraints to limit malicious payload behavior
- Observability / operational considerations:
  - Track queue depth, conversion success/failure ratio, and per-format performance
- Dependencies:
  - 30, 40
- Constraints / notes:
  - Should remain format-agnostic at control level to avoid coupling orchestration to conversion internals

### 30 — File and Artifact Management

- Category:
  - data persistence
- Purpose:
  - Manage source file intake, temporary processing artifacts, and final converted outputs with controlled access.
- Responsibilities:
  - Store uploaded source files and converted outputs
  - Provide scoped read/write handles for conversion processing
  - Enforce artifact lifecycle and retention policies
  - Preserve integrity metadata for uploaded and produced files
- Interfaces:
  - Incoming:
    - Upload/write requests for source files
    - Read/write requests from conversion processing
    - Download/read requests for completed outputs
  - Outgoing:
    - File references and access tokens to trusted internal components
    - Artifact lifecycle events for expiration and cleanup
- Data / state:
  - Binary artifacts, integrity checksums, size/type metadata, retention markers
- Interactions:
  - User-facing:
    - Indirect through secure upload and download capability
  - Internal synchronous:
    - Access validation and artifact metadata retrieval
  - Internal asynchronous:
    - Retention and cleanup event handling
- Security / access considerations:
  - Enforce strict access boundaries between tenant/user contexts
  - Prevent direct public exposure of stored artifacts
- Observability / operational considerations:
  - Monitor storage usage trends, failed transfers, and cleanup backlog
- Dependencies:
  - 20, 40
- Constraints / notes:
  - Must support both text and geo file families included in scope

### 40 — Conversion Processing Fabric

- Category:
  - domain service
- Purpose:
  - Execute document and geospatial file conversions asynchronously and return normalized outcomes.
- Responsibilities:
  - Consume conversion jobs and fetch source artifacts
  - Select and execute the right conversion pathway by format pair
  - Emit conversion outputs and structured failure diagnostics
  - Return completion events and processing metadata
- Interfaces:
  - Incoming:
    - Conversion execution commands with source reference and target format
  - Outgoing:
    - Completed artifact writes
    - Job completion/failure events with reason details
- Data / state:
  - Ephemeral task execution state and conversion diagnostics
  - Optional reusable mapping/configuration for supported format transformations
- Interactions:
  - User-facing:
    - None
  - Internal synchronous:
    - Reads/writes via artifact management
  - Internal asynchronous:
    - Receives job commands and emits completion events
- Security / access considerations:
  - Run conversion workloads in isolated execution boundaries
  - Restrict processor permissions to least-privilege artifact access
- Observability / operational considerations:
  - Capture per-format execution time, failure taxonomy, and retry behavior
- Dependencies:
  - 20, 30
- Constraints / notes:
  - Must gracefully reject unsupported source/target combinations
- Principal alternative (optional)
  - Split processing into two fabrics (text and geo). This improves specialization but increases operational overhead and coordination complexity.

## System interaction summary

- Primary request / control paths:
  - User submits file and desired format through 10, which calls 20 to validate and create a conversion job. 20 orchestrates processing through 40 and exposes status back to 10.
- Primary data flows:
  - Source artifacts are uploaded and referenced through 30, consumed by 40 during conversion, and written back as output artifacts for retrieval via 20 and 10.
- Primary event flows:
  - 20 dispatches asynchronous conversion commands to 40; 40 emits completion/failure events; 20 updates lifecycle state and notifies client-facing status.

## System-wide concerns

- Security and access control:
  - Request-level authorization for all job and artifact operations
  - Isolated conversion execution to limit impact of malformed or hostile inputs
  - Scoped artifact access with short-lived capabilities
- Reliability and recovery:
  - Asynchronous job model with retriable failures for transient processing errors
  - Durable tracking of job lifecycle states
  - Cleanup and retention policy to avoid stale artifacts and uncontrolled growth
- Observability and operations:
  - End-to-end tracing from submission through processing completion
  - Operational dashboards for throughput, error rate, and queue depth
  - Audit trail for conversion requests, accesses, and outcomes
- Performance and scalability:
  - Horizontal scaling of conversion processors based on backlog pressure
  - Segregation of control-plane requests from heavy conversion workloads
  - Efficient artifact transfer patterns to minimize repeated large-file movement
- Compliance / audit / governance:
  - Data retention windows and deletion guarantees for uploaded/converted documents
  - Conversion activity logging aligned with organizational audit needs

## Open questions
- Should this architecture include authenticated user accounts at launch, or support anonymous conversion sessions with short-lived access scopes?
- What is the maximum file size target and expected daily conversion volume that should guide capacity and queue policies?
- Are there any jurisdictional or data residency constraints that affect artifact placement and retention?
