# Websockets in C
## Sockets
### An	interface	between	application	and	network	
  * The	application	creates	a	socket	
  * The	socket	type	dictates	the	style	of communication
#### Reliable	vs.	Best	Effort
  - Reliable Websockets: In reliable websockets, data transmission is guaranteed. This means that the data sent over the websocket connection will be received by the other party, and in the correct order. If there are any errors or packets lost during transmission, the protocol ensures that they are detected and retransmitted. This reliability is achieved through mechanisms such as acknowledgments and retransmissions.
  - Best Effort Websockets: In best effort websockets, there is no guarantee of reliable data transmission. Data packets are sent from one endpoint to another with the best effort, but there is no mechanism to ensure that they are received or that they arrive in the correct order. This approach prioritizes low latency and simplicity over reliability. While best effort websockets may be suitable for applications where occasional data loss or out-of-order delivery is acceptable, they are not ideal for applications that require reliable communication, such as real-time gaming or financial transactions.
#### Connection-Oriented	vs.	Connectionless
  - Connection-Oriented Websockets:
    - In connection-oriented communication, there is an established connection between the client and the server before any data transfer occurs.
    - In the context of websockets, this means that there is a handshake process (WebSocket handshake) where the client and server negotiate and establish a persistent connection.
    - Once the connection is established, both parties can send messages to each other at any time without needing to re-establish the connection for each message.
    - Connection-oriented communication is typically more reliable and provides features such as guaranteed delivery and in-order delivery of messages.
  - Connectionless Websockets:
    - In contrast, connectionless communication does not require a pre-established connection before sending data.
    - In the context of websockets, a connectionless approach would mean that each message sent by the client is treated as an independent unit without any prior setup or handshake.
    - This approach is less common in websockets because the protocol itself is inherently connection-oriented. However, in other networking protocols like UDP (User Datagram Protocol), which is connectionless, messages are sent without establishing a connection first.
    - Connectionless communication is often used in scenarios where speed and simplicity are prioritized over reliability, as there is no overhead associated with establishing and maintaining connections.
<div>
**Once configured, the application	can	pass	data	to	the	socket	for	network	transmission receive	data	from	the	socket	(transmitted	through	the	network	by	some	other	host)**
</div>
