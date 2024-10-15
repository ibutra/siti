[comment]: vim:tw=80

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

```ascii
                                    ┌────┐
                                 ┌─►│node│◄─┐
        ┌────────────────┐       ▼  └────┘  ▼      ┌────────────────┐
        │┌───────────────┴┐   ┌────┐      ┌────┐   │┌───────────────┴┐
        └┤Service/Consumer│◄─►│node│◄────►│node│◄─►└┤Service/Consumer│
         └────────────────┘   └────┘      └────┘    └────────────────┘
```


### Certificates

TLS will be used for communication and x509 certificates. The certificates will
be self signed/created and not a chain but single specific certificates will be
trusted. 

The certificate will have a limited lifetime and must be renewed with the other
nodes. This should happen automatically and transparent for the user.

It must also be possible to revoke a certificate if a node is removed from the
siti network. It should be sufficient to delete it from all nodes and also save
that it was deleted with timestamp so that currently offline nodes replicate the
deletion. To prevent a removed node joining a node that was offline during
deletion a node shall try to connect to all know nodes and sync the network
state with them before accepting and routing actual traffic.
