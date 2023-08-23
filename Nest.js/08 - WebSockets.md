# WebSockets in Nest.js

WebSockets are a communication protocol that provides full-duplex communication channels over a single TCP connection. Nest.js supports WebSockets out of the box, making it easy to implement real-time communication in your applications.

## Setting Up WebSockets

To use WebSockets in Nest.js, you'll need to install the required package:

```bash
npm install @nestjs/websockets

```

## Creating WebSocket Gateway

Gateways are classes responsible for handling WebSocket connections and events. To create a WebSocket gateway, you'll use the @WebSocketGateway() decorator.

```javascript
// chat.gateway.ts
import { WebSocketGateway, WebSocketServer, SubscribeMessage, MessageBody } from '@nestjs/websockets';
import { Server } from 'socket.io';

@WebSocketGateway()
export class ChatGateway {
  @WebSocketServer()
  server: Server;

  @SubscribeMessage('message')
  handleMessage(@MessageBody() message: string) {
    this.server.emit('message', message);
  }
}

```

## Creating WebSocket Gateway

Gateways are classes responsible for handling WebSocket connections and events. To create a WebSocket gateway, you'll use the @WebSocketGateway() decorator.

```javascript
// chat.gateway.ts
import { WebSocketGateway, WebSocketServer, SubscribeMessage, MessageBody } from '@nestjs/websockets';
import { Server } from 'socket.io';

@WebSocketGateway()
export class ChatGateway {
  @WebSocketServer()
  server: Server;

  @SubscribeMessage('message')
  handleMessage(@MessageBody() message: string) {
    this.server.emit('message', message);
  }
}

```

## Connecting to WebSockets

To establish a WebSocket connection from the client, use the socket.io-client library or any other WebSocket client library. Here's an example using socket.io-client

```javascript
import { io } from 'socket.io-client';

const socket = io('http://localhost:3000');
socket.on('message', (data) => {
  console.log('Received message:', data);
});

```

## Using the WebSocket Gateway

To use the WebSocket gateway in your application, you'll need to include it in a module's providers array.

```javascript
// app.module.ts
import { Module } from '@nestjs/common';
import { ChatGateway } from './chat.gateway';

@Module({
  providers: [ChatGateway],
})
export class AppModule {}

```

## Conclusion

WebSockets provide a powerful mechanism for real-time communication between clients and servers. By following this crash course, you've learned how to create a WebSocket gateway, handle WebSocket events, and connect to WebSockets from a client. This knowledge will help you implement real-time features in your Nest.js applications.