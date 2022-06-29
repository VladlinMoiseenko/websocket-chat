# Websocket chat Example

Implementation in Rust using actix, actix-web, actix-broker

Пример основан на [chat-broker](https://github.com/actix/examples/tree/master/websockets/chat-broker )


- Chat Server Actor — это системная служба, которая работает в том же потоке, что и HttpServer/WS Listener.

- [actix-broker](https://github.com/Chris-Ricketts/actix-broker) crate  используется для облегчения отправки сообщений между сеансом чата и актерами сервера, когда сеанс не требует ответа.

- Клиенту не требуется отправлять сообщения Ping. Актер сервера автоматически очищает мертвые сеансы.

## Server

Чат-сервер прослушивает входящие TCP-соединения. Сервер может получить доступ к нескольким типам сообщений:

- `/list` - список всех доступных комнат
- `/join name_room` - присоединиться к комнате, если комнаты нет, создать новую
- `/name name` - установить имя сеанса
- `some message` - просто строка, отправить сообщение всем пирам в одной комнате

Для запуска сервера используйте команду:

```sh
cd websocket-chat

cargo run
```

## WebSocket Browser Client

Open url: http://localhost:8080/