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
