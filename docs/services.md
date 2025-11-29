# Services

The **Services** group contains the runtime components of ThermoBus:
independent executable services that expose APIs, process messages, or act as
entry points for clients and devices.

It currently includes:

---

## ThermoBus.Api
The main HTTP API used to manage devices and receive telemetry.

Responsibilities:
- Exposes REST endpoints
- Calls Application-layer use cases
- Publishes messages to the Messaging layer
- Returns clean DTOs (from ThermoBus.Contracts)

Tech: ASP.NET Core Web API.

---

## ThermoBus.Gateway
YARP-based reverse proxy serving as the entry point of the system.

Responsibilities:
- Routes incoming requests to internal services
- Simplifies client integration
- Enables unified logging, rate limiting, versioning, and security

Tech: YARP (Yet Another Reverse Proxy).

---

## ThermoBus.Workers.Ingestion
Background worker that processes telemetry streams or messages.

Responsibilities:
- Subscribes to messages (e.g., telemetry events)
- Executes Application use cases
- Stores data or triggers KPI calculations
- Runs continuously as a hosted service

Tech: .NET Worker Service + Messaging Abstractions.

---

These services run independently and communicate via the message bus or the API,
representing the operational layer of ThermoBus.
