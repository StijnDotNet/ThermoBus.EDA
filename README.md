# ThermoBus.EDA

**ThermoBus** is an educational, production-inspired **Event-Driven Architecture (EDA)** demo project built with **.NET 10**.  
It simulates a fleet of temperature-controlled storage units (refrigerated trucks, containers, cold rooms) that send telemetry.  
Messages are processed through a lightweight, pluggable service bus and consumed by multiple independent services.

This project demonstrates:
- Clean Architecture (Domain / Application / Infrastructure)
- Event-Driven Architecture principles
- Loose coupling via service bus abstractions
- Publisher/subscriber flows
- API Gateway (YARP)
- Worker Services
- Simulated telemetry ingestion

It is designed as a **portfolio-ready learning/demo project** that recruiters and lead developers can quickly understand.

---

# 🚀 Key Features

- **Clean Architecture** separation  
  Domain logic isolated from infrastructure, UI, and messaging.

- **Pluggable messaging**  
  Interfaces in `ThermoBus.Messaging.Abstractions`.  
  Default implementation: in-memory bus (development-friendly).  
  Can be swapped later for RabbitMQ/Kafka/Azure Service Bus.

- **API Gateway**  
  Built with YARP to route external requests to internal services.

- **Background worker ingestion**  
  Message consumers and telemetry processing.

- **Simulator**  
  Generates realistic telemetry events (temperatures, alerts, thresholds crossed).

---

# 🏗️ Solution Layout

The solution is divided into logical groups (solution folders in Visual Studio).  
Actual project folders live under `/src`.

| Group       | Contains                                      | Purpose |
|-------------|-----------------------------------------------|---------|
| **Core**    | Domain, Application, Infrastructure, Contracts | Business rules, use cases, persistence adapters |
| **Messaging** | Abstractions, InMemory implementation        | Pluggable service bus system |
| **Services**  | API, Gateway, Worker                         | Runtime services that expose APIs or consume messages |
| **Tools**     | Simulator                                    | Generates test telemetry |
| **Tests**     | ThermoBus.Tests                              | Unit & integration tests |

Details for each group are documented in the `/docs` folder.

---

# 📚 Detailed Documentation

For a deep dive into each group:

- [Core](docs/core.md)
- [Messaging](docs/messaging.md)
- [Services](docs/services.md)
- [Tools](docs/tools.md)

And architectural notes:

- [Architecture Overview](docs/architecture.md) *(optional, you can add this later)*
- [Event Flow Examples](docs/event-flow.md) *(optional)*
- [Sequence Diagrams](docs/sequence-diagrams.md) *(optional)*

---

# 🧩 Technical Stack

- **.NET 10**
- ASP.NET Core Web API
- Worker Service (background processing)
- YARP (reverse proxy / API Gateway)
- In-memory message bus
- EF Core (optional future extension)
- C# 13

---

# ▶️ How to Run the Project

> These commands assume you run services individually.  
> Docker Compose support can be added later.

### 1. Build everything
```bash
dotnet build
