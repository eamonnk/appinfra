An event-driven architecture consists of event producers that generate a stream of events, and event consumers that listen for the events.

Events are delivered in near real time, so consumers can respond to events immediately as they occur. Producers are decoupled from consumers — a producer doesn't know which consumers are listening. Consumers are also decoupled from each other, and every consumer sees all of the events. This differs from a Competing Consumers pattern, where consumers pull messages from a queue and a message is processed just once (assuming no errors). In some systems, such as IoT, events must be ingested at very high volumes.

<p style="text-align:center;"><img src="../Linked_Image_Files/eventdriven.png" alt="A image representing the event driven architectural model."></p>

### When to use this architecture
Consider an this architecture for:
- Multiple subsystems which must process the same events.
- Real-time processing with minimum time lag.
- Complex event processing, such as pattern matching or aggregation over time windows.
- High volume and high velocity of data, such as IoT and real-time systems.

### Benefits
- Producers and consumers are decoupled.
- No point-to point-integrations. It's easy to add new consumers to the system.
- Consumers can respond to events immediately as they arrive.
- Highly scalable and distributed.
- Subsystems have independent views of the event stream.

> :information_source: An event-driven architecture is generally best suited to IoT and real-time systems.
