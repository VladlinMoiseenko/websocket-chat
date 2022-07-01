# Websocket Chat Example

[README_RUS](https://github.com/VladlinMoiseenko/websocket-chat/blob/master/README_RUS.md ): Русская версия README.

Implementation in Rust using actix, actix-web, actix-broker

The example is based on [chat-broker](https://github.com/actix/examples/tree/master/websockets/chat-broker )


- Chat Server Actor is a System Service that runs in the same thread as the HttpServer/WS Listener.
- The [actix-broker](https://github.com/Chris-Ricketts/actix-broker) crate is used to facilitate the sending of some messages between the Chat Session and Server Actors where the session does not require a response.
- The Client is not required to send Ping messages. The Chat Server Actor auto-clears dead sessions.

## Server

Chat server listens for incoming tcp connections. Server can access several types of message:

- `/list` - list all available rooms
- `/join name` - join room, if room does not exist, create new one
- `/name name` - set session name
- `some message` - just string, send message to all peers in same room

To start server use command:

```sh
cd websocket-chat

cargo run
```

### WebSocket Browser Client

Open url: http://localhost:8080/

### WebSocket Android Client

[Websocket Chat Android Client](https://github.com/VladlinMoiseenko/websocket-chat-android-client )
