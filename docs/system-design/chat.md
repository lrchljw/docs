---
title: Chat
---

# Chat

## Questions

One to one, or group chat
How many users in one group
How many messages per seconds
What is the size of one message?
How many delays can accept?
Should users receive notification when they are not online.

## Requirements and Scope

- Search by words from message history

### Tech requirements

- Exactly once delivery
- Max size of one message limited to 1MB

## Architecture from simple to complex

### Single Server

Client A -> Chat Service -> Client B

SPOF

- Client connects to the nearest server based on latency

  - Do reseach on how CDN providers achieve this

- Reconnect when connection is lost
  - Reasons for disconnection
    - Client network issue
    - Server network issue
    - Server is down

## Techniques that enables Server sending messages to clients

- **Polling**
- **Long Polling**
- **WebSockets**

## References

- [How Discord Stores Trillions of Messages](https://discord.com/blog/how-discord-stores-trillions-of-messages)

![img](/img/how-discord-stores-billions-of-messages.jpeg)

- [How League of Legends Scaled Chat to 70 million Players](https://highscalability.com/how-league-of-legends-scaled-chat-to-70-million-players-it-t/)

- [Scaling WebSocket in Go and beyond](https://centrifugal.dev/blog/2020/11/12/scaling-websocket)

- [Why we chose Kafka for the Trello socket architecture](https://www.atlassian.com/engineering/why-we-chose-kafka)

- [Tarantool: when it takes 500 lines of code to notify a million users](https://hackernoon.com/tarantool-when-it-takes-500-lines-of-code-to-notify-a-million-users-11d340523493)

- [A Million WebSockets and Go](https://www.freecodecamp.org/news/million-websockets-and-go-cc58418460bb/)

- [NATS Unveiled: The Secret to Scalable Chat Apps on iOS](https://ddh4r4m.medium.com/nats-unveiled-the-secret-to-scalable-chat-apps-on-ios-721df3593147)

- [Building a live chat with Go, NATS, Redis and Websockets](https://ribice.medium.com/building-a-live-chat-with-go-nats-redis-and-websockets-cb3edbc940ca)
