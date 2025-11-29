# Core

The **Core** group contains all the business logic of the ThermoBus system,
structured according to Clean Architecture principles.  
This code is independent from infrastructure, UI, databases, or messaging
technologies.

It includes the following projects:

---

## ThermoBus.Domain
Domain entities, value objects, domain services, and domain events for the
temperature-controlled fleet domain.

Typical content:
- `RefrigeratedUnit`, `TelemetrySample`, `TemperatureThreshold`
- Domain rules and invariants
- Domain events such as `ThresholdExceededEvent`

---

## ThermoBus.Application
Application layer orchestrating use cases.

Responsibilities:
- Handles commands and queries (CQRS style)
- Coordinates domain logic
- Defines interfaces for persistence, messaging, and external systems

Examples:
- Process incoming telemetry
- Register a machine
- Trigger KPI recalculations

---

## ThermoBus.Contracts
Data transfer objects shared between services and external clients.

Includes:
- API request/response models
- Messaging contracts for events and commands
- Shared enums

The goal is to avoid leaking domain entities outside the application boundary.

---

## ThermoBus.Infrastructure
Concrete implementations of interfaces defined in the Application layer.

Typical implementations:
- Persistence (e.g. EF Core repositories)
- Messaging integrations
- Configuration providers
- Logging and adapters

Infrastructure depends on Application, never the other way around.

---

This group represents the stable business core of ThermoBus.  
It can be reused or extended without impacting higher-level services.