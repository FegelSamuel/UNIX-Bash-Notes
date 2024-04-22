# Websockets in General
# Sockets
## An	interface	between	application	and	network	
  * The	application	creates	a	socket	
  * The	socket	type	dictates	the	style	of communication
### Reliable	vs.	Best	Effort
  - Reliable Websockets: In reliable websockets, data transmission is guaranteed. This means that the data sent over the websocket connection will be received by the other party, and in the correct order. If there are any errors or packets lost during transmission, the protocol ensures that they are detected and retransmitted. This reliability is achieved through mechanisms such as acknowledgments and retransmissions.
  - Best Effort Websockets: In best effort websockets, there is no guarantee of reliable data transmission. Data packets are sent from one endpoint to another with the best effort, but there is no mechanism to ensure that they are received or that they arrive in the correct order. This approach prioritizes low latency and simplicity over reliability. While best effort websockets may be suitable for applications where occasional data loss or out-of-order delivery is acceptable, they are not ideal for applications that require reliable communication, such as real-time gaming or financial transactions.
### Connection-Oriented	vs.	Connectionless
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


![image](https://github.com/FegelSamuel/UNIX-Bash-Notes/assets/126997597/7beef580-253e-4846-a00b-109622d235f5 "Two Main Types of Sockets")

<br>

# Connection Conceptual Stuff
## Active Participant
* Initiates conversation between machines
## Passive Participant
* Is the receiving end (can still send stuff, just didn't start the interaction)
* **Passive Participant** must `bind` and `listen` before the **Active Participant** issues a `connect`. Then, the **Passive Participant** can `accept` the connection request. If that does happen, `data transfer` can occur.
* The accepted connection is on a new socket
* The old socket continues to listen for other active participants


![Connection Setup](https://github.com/FegelSamuel/UNIX-Bash-Notes/assets/126997597/b384ecf5-0f7f-49a7-ae55-37e249329fb9)



# The C Code Part
## Making a Socket
```C
int s = socket(domain, type, protocol);
// s: socket descriptor is an int (like file-handle)
// domain: int variable, communication domain. Generally, we are going to use IPV4 (it's dated because IPV6 but some systems still use it)
// type: either SOCK_STREAM or SOCK_DGRAM
// protocol: usually set to 0; specifies protocol (ssh is 22)
```
**NOTE:	socket	call	does	not	specify	where	data	will	be	coming	from,	nor	where	it	will	be	going	to	–	it	just	creates	the	interface!**
## Associating and (may exclusively) reserving a port for use by a Socket
```C
int status = bind(sockid, &addrport, size);
// size: Size in bytes of the addrport struct
// sockaddr: struct sockaddr,	the	(IP)	address	and	port	of	the	machine	(address	usually	set	to	INADDR_ANY –	chooses	a	local	address)	
// sockid:	integer,	socket	descriptor	(In the previous code, that is the int s)
// status: Any integer; will return -1 if failed
```
You can actually skip doing this bind stuff if: 
<br>
**SOCK_DGRAM**: When sending information, we don't need to bind anything. The Operating System handles that for us
<br>
***YOU WILL STILL NEED TO BIND WHEN USING SOCK_DGRAM AND RECIEVING INFORMATION***
<br>
**SOCK_STREAM**: Destination	determined	during	connection	setup
<br>
Don’t	need	to	know	port	sending	from	(during	connection	setup,	receiving	end	is	informed	of	port)
<br>
## Connection Setup
### Listening
Listeners are non-blocking, so they will return immediately
```C
int status = listen(sock, queuelen);
// status is 0 if listening, -1 if error
// sock: int, socket descriptor (with respect to the previous code, s is what we would be passing in)
// queuelen: Queue Length, integer,	number	of	active	participants	that	can	“wait”	for	a	connection in a line
```
### Accepting
Accepts are blocking, so they will wait until returning
```C
int s = accept(sock, &name, &namelen);
// s:	integer,	the	new	socket	(used	for	data-transfer)
// sock:	integer,	the	orig.	socket	(being	listened	on)
// name:	struct sockaddr,	address	of	the	active	participant
// namelen:	sizeof(name):	value/result	parameter; YOU NEED TO APPROPRIATELY SET THIS BEFORE CALLING THE ACCEPT FUNCTION; It's adjusted by the OS when returning (that's why we are passing by ref)
```
### Connect
```C
int status = connect(sock, &name, namelen); // THIS IS BLOCKING
// status = 0 if successful
```





