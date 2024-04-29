# Problem
* Create two different sockets
  * One has UDP and the other has TCP
* Remember to bind the port with the port number and network address.
  * You will need to bind twice
* Basically, you can now accept UDP and TCP
1. “echo_s” should reply to any client connected to one of its ports with the same message it receives. 
2. “echo_s” must support both TCP and UDP connections from clients, on the same port number. 
3. Your echo server must accept messages on multiple well-known port numbers (max 3). The server must 
run from the command-line with the port numbers to listen on as the command-line arguments. At a 
minimum, there must be one port number specified. Here's the required command-line format 
(arguments between [] are optional): 
$> echo_s <port1> [<port2> <port3>]
`well-known`: The server specifies the port number being used by having port1 and port2 and port3

# nc
nc is used as echo server
```bash
nc -e /bin/cat -k -u -l 1235
```
nc is used as echo client
```bash
nc -u 127.0.0.1 1235
```
Let's say you want to set up a simple server that listens on port 12345 and echoes back any message it receives. You can achieve this using nc in listen mode (-l) with the -p option to specify the port:
```bash
nc -l -p 12345
```
Now, your server is listening on port 12345.

<br>

To connect to this server from another terminal or machine, you can use nc in another terminal in client mode. You need to specify the IP address of the server and the port it's listening on:
```bash
nc <server_ip> 12345
```




