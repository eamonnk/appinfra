An *event-driven* architecture consists of *event producers* that generate a stream of events, and *event consumers* that listen for the events.

<p style="text-align:center;"><img src="../Linked_Image_Files/eventdriven.png" alt="A representation of the event-driven architectural model."></p>

Events are delivered in near real time, so consumers can respond immediately to events as they occur. Producers are decoupled from consumers, so they don't know which consumers are listening. 

Consumers are also decoupled from each other, and every consumer sees all of the events. This differs from a competing consumers pattern, where consumers pull messages from a queue and a message is processed just once (assuming no errors). In some systems such as IoT, events must be ingested at high volumes.

### When to use this architecture
Consider this architecture for:
- Multiple subsystems that must process the same events.
- Real-time processing with minimum lag time.
- Complex event processing, such as pattern matching or aggregation over time.
- High volume and high velocity of data, such as IoT.

### Benefits
The benefits of this architecture are:

- Producers and consumers are decoupled.
- There's no point-to point-integrations. It's easy to add new consumers to the system.
- Consumers can respond to events immediately as they arrive.
- The architecture is highly scalable and distributed.
- Subsystems have independent views of the event stream.
