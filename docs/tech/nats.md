---
title: NATS
description: record my basic understanding of NATS
---

# NATS

- Nats Core
  - Using Raft consensus protocol to sync subjects across the cluster
- JetStream
  - Persistent storage using local disk
  - Key/Value store

## Nats Core

### Patterns

#### Request/Reply

- Used to contruct Services that respond to Requests
- Requester and replier don't need to know each other, they only care about the subject
- Advantages over typical RPC techniques, which assume a one-to-one connection between the requester and the replier

```sh
nats reply 'subject' 'response'
nats req 'subject' 'data payload can be string/json/bson, etc, nats is payload agnostic'
```

#### Pub/Sub

```sh
nats sub 'subject'
nats pub 'subject' 'data payload'
```

- Fan in

  - One subscriber, multiple publishers

- Fan out

  - One publisher, multiple subscribers
  - Each subscriber gets a copy of the message

- Queue group

  - Multiple subscribers, only one subscriber in the group gets the message
  - Nats evenly distributes load among the subscribers in the group
  - No need standalone load balancer

- Wildcards
  - `>` to match the rest of the subject
  - `nats sub >` to observe all messages

> Nats cli

## References

- [Understanding NATS Architecture](https://github.com/nats-io/nats-general/blob/main/architecture/ARCHITECTURE.md)
- [JetStream](https://docs.nats.io/nats-concepts/jetstream)

- [Distributed messaging with NATS](https://dev.to/karanpratapsingh/distributed-messaging-with-nats-3jg3)

- [Using NATS to build a scalable Websocket server](https://medium.com/@14domino/using-nats-to-build-a-very-functional-websocket-server-8f4de44c3f12)
