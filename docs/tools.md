# Tools

The **Tools** group contains helper applications used for development and
demonstration purposes. These tools are not part of the production system but
are essential for testing and simulation.

It currently includes:

---

## ThermoBus.Simulator
A standalone console application that simulates refrigerated units and sends
fake telemetry into the system.

Capabilities:
- Periodically generates temperature samples
- Sends telemetry to the API or publishes directly to the message bus
- Configurable number of simulated devices
- Used to demonstrate the end-to-end Event-Driven Architecture flow

Ideal for:
- Testing message ingestion
- Demoing real-time behaviour
- Validating threshold logic

---

Tools improve developer experience and help validate the architecture without
requiring real hardware.
