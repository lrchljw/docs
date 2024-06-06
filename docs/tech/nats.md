---
title: NATS
description: record my basic understanding of NATS
---

# NATS

- Nats Core
- JetStream
  - Persistent storage
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
