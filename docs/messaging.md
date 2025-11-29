# Messaging

The **Messaging** group contains the abstractions and implementations
of the message bus used by ThermoBus.  
The design allows the system to run with a lightweight in-memory bus during
development, while enabling easy replacement with a real broker later
(e.g., RabbitMQ, Azure Service Bus, Kafka).

It includes:

---

## ThermoBus.Messaging.Abstractions
Defines all messaging interfaces and foundational types.

Includes:
- `IMessagePublisher`
- `IMessageSubscriber`
- `IMessageHandler<T>`
- Envelope and metadata types
- Base classes for strongly-typed events and commands

Purpose:  
Allow services to publish and consume messages without referencing any
specific technology.

---

## ThermoBus.Messaging.InMemory
In-memory implementation of the messaging abstractions.

Characteristics:
- No external dependencies
- Instant delivery (synchronous or queued)
- Perfect for local development and automated tests

Used by:
- API
- Workers
- Simulator

Later, a real messaging provider can be added in a new project without changing
any other layer.

---

Messaging is central to ThermoBus’ Event-Driven Architecture and ensures loose
coupling between services.