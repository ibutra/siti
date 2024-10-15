# Siti

A simpler but also less feature full overlay network.

## Notes

### Components

| Component | Description                                                                                          | Siti             |
| ---:      | ---                                                                                                  | ---              |
| Node      | A siti network is compromised of one or more nodes which mesh with each other and route the traffic. | internal         |
| Service   | Provider of "something" that will be routed through the siti network and used by *consumers*.        | external(config) |
| Consumer  | Uses provided services through the siti network                                                      | external(config) |
| Policy    | Access rights granting consumers access to services.                                                 | config           |

### Network

Every Node replicates it's configuration to all other nodes. I.e. adding and
authenticating an additional node to a single node will be replicated to all
other nodes.

                                    ┌────┐
                                 ┌─►│Node│◄─┐
        ┌────────────────┐       ▼  └────┘  ▼      ┌────────────────┐
        │┌───────────────┴┐   ┌────┐      ┌────┐   │┌───────────────┴┐
        └┤Service/Consumer│◄─►│node│◄────►│node│◄─►└┤Service/Consumer│
         └────────────────┘   └────┘      └────┘    └────────────────┘

