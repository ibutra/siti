# Siti

A simpler but also less feature full overlay network.

## Notes

### Networking


| Component  | Description                                                                                   | Siti             |
| ---        | ---                                                                                           | ---              |
| Controller | Know who to trust and have information about whole network. Also route like the router.       | internal         |
| Router     | Route traffic inside the network  Can be entry, exit or transfer for ang traffic.             | internal         |
| Service    | Provider of "something" that will be routed through the siti network and used by *consumers*. | external(config) |
| Consumer   | Uses provided services through the siti network                                               | external(config) |
| Policy     | Access rights granting consumers access to services.                                          | config           |
