---
pcx_content_type: concept
title: WebSockets in Durable Objects
---


# WebSockets in Durable Objects

Durable Objects are a coordinated state tool for [Cloudflare Workers](/workers/), which are often used in parallel with WebSockets to persist state over multiple clients and connections. 

If your application needs to coordinate among multiple WebSocket connections, such as a chat room or game match, you will need to [create a Durable Object](/durable-objects/learning/create-durable-object-stubs/), so clients send messages to a single-point-of-coordination. 

As part of Durable Objects, Workers can act as WebSocket endpoints – including as a client or as a server. Previously, Workers could proxy WebSocket connections on to a back-end server, but could not speak the protocol directly.

WebSockets are most useful when combined with Durable Objects. When a client connects to your application using a WebSocket, you need a way for server-generated events to be sent back to the existing socket connection. 

With Durable Objects, you can forward the WebSocket to an Object. Messages can then be addressed to that Object by its [unique ID](/durable-objects/learning/access-durable-object-from-a-worker/#1-create-durable-object-ids), and the Object can then forward those messages down the WebSocket to the client.

Durable Objects can use the web standard APIs described in [Using WebSockets](/workers/learning/using-websockets/). When using a Durable Object to terminate a WebSocket (as opposed to using it as a WebSocket client) the [Hibernatable WebSockets API](/durable-objects/api/hibernatable-websockets-api/) has significant advantages and should be preferred over the web standard APIs. 

Refer to [Cloudflare Edge Chat Demo](https://github.com/cloudflare/workers-chat-demo) for an example of WebSockets in action within Durable Objects.