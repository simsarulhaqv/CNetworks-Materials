## Application layer

### Application architectures:
* Client server
	* Server:
		* Always on host
		* Permanent IP address
	* Clients:
		* Communicate with servers
		* May be intermittendly connected
		* May have dynamic IP addresses.
		* Do not communicate directly with each other.
* P2P architecture
	* Arbitary end systems directly communicate.
	* No directly on server.
	* Peers request service from other peers, provide service in return to other services.
	* Self scalability: New peers can introduce new service capability as well as new servoce demands.
	* Peers are intermittenly connected and change IP address.

### Process communicating
* Process is a program running in a host.
* Within the same host, two process communicate using inter-process communication.
* Process in different host communicate by exchanging messages.
* Client process is the process that initiate communication.
* Server process is the process that waits to be contacted.
* Applications with P2P architecture have client and server process.

####Sockets
* Process send/recieve  message to/from its socket.
* Socket is in the application layer, which is managed by the app developer.
* All other layers are managed by the OS.

### Addressing processes:
* to recieve message, process must have a identifier.
* IP address is not enough to identify the process, as many process run on the same host.
* Identifier includes both IP address and port numbers associated whth process on host.

### App-layer protocol:
* It defines the following:
	* Types of messages exchanged
	* Message syntax
	* Message semantics
	* Rules
	* protocols

### Trasport layer service assumptions:
* This layer assumes the following services from the transport layer.
	* Data integrity: Data must not be lost from various files. It can tolerate some loss from some apps like audio.
	* Timing : require low delay
	* Throughput: Require a minimum throughput to be effective
	* Security: encryption

### Internet transport protocols services:
* TCP service:
	* reliable transport
	* flow control: Sender won't overwhelm receiver
	* Congestion control
	* Does not provide timing, minimum throughput guarantee, security.
	* Connection oriented: Setup required between server and client processes
* UDP service:
	* Unreliable data transfer
	* Does not provide reliability, flow control, congestion control, timing, throughput guarantee, security, or connection setup.

### Securing TCP:
* TCP and UDP have no encryption
* SSL:
	* Provides encrypted TCP connection
	* data integrity
	* end-point authentication.
* SSL is at app layer.
* SSL socket API

### Web and HTTP
* Web page consist of objects
* Each objects is addressable by URL
* HTTP: Web's application layer protocol.
	* Client server model.
	* HTTP is stateless, means server maintains no information about past client requests.
	* Protocols that maintains state are complex.
	* uses TCP
	* Client initiates TCP connection to server, port 80.
	* Server accepts TCP connection from the client.
	* HTTP messages then exchanged,
	* TCP connection closed.

### HTTP connections:
* Non-persistent HTTP:
	* At most one object sent over TCP connection , Connection then closed.
	* Downloading multiple objects require multiple connections.
* Persistent HTTP:
	* Multiple objects can be sent over single TCP connection between client and server.

### Non-persistent HTTP: response time:
* Require one RTT to initiate TCP connection.
* Reqquire one RTT for HTTP request and few bytes of HTTP response to return.
* Plus there will be file transmission time
* So, non persistent HTTP response time = 2RTT + file transmission time.

#### Method types in HTTP:
* HTTP/1.0 : GET, POST, HEAD
* HTTP/1.1 : GET,POST,HEAD,PUT,DELETE

#### HTTP respomse status codes:
* 200 OK : Success
* 301 Moved Permanently : Requested object moved to new llocation
* 400 Bad request :  Request message not understood by server
* 404 Not found : Reqquest document not found on this server
* 505 HTTP Version Not Supported
 
### User-server state: Cookies
* Cookies have four components:
	* Cookie header line of HTTP response message
	* Cookie header line in next HTTP request message
	* Cookie file kept on user's host, managed by user's browser.
	* Backend database at web-site
* Cookies keeping state.
* Cookies can be used for:
	* Autherization
	* Shopping carts
	* recommendations
	* User session state
* Cookies permit sites to learn about you a lot

### Web caches (Proxy server):
* Goal is to satisfy client request without involving the origin server.
* User will initially ser browser to access web via cache
* Cache can act as both client and server.
* Cache can reduce response time for client request.

###FTP
* TCP control connection, server port 21
* TCP data connection, server port 20
* Initially FTP client contacts FTP serer at port 21, using TCP connection to transfer another file.

### Electronic mail
* Three major components:
	* User agents
	* Mail servers
	* simple mail transfer protocol: SMTP
* User agent: aka "mail reader"
* Mail servers:
	* Mailbox: conatan incoming messages for the user.
	* Message queue: contain outgoing mail messages.
* SMTP protocol
	* Uses  TCP to reliably traansfer email message from client to server, port 25
	* Three phases of transfer:	
		* Handshaking
		* Transfer of messages
		* Closure
	* After recieving the messsage in the inbox, the user invokes thier user agent to read the message.
	* SMTP uses persistent connections.
	* Requires message to be in 7-bit ASCII
	* SMTP uses CRLF.CRLF to determine end of message

### Mail access protocols
* POP: Post office protocol
* IMAP: Internet mail access protocol
* HTTP

###DNS:
* Distributed database
	* Implemented in hieraarchy of many name servers
* DNS services:
	* hostname to IP address translation
	* host aliasing
* Top-level doamin (TLD) servers. eg: com, org ...
* Autheritative DNS servers: Orgnizations own DNS server making hostname to IP mapping.
* Local DNS name server. When host makes DNS query, it is first send to Local DNS name server.
	* Iterated query: Contacted server will reply with the name of the server to contact.
	* Recursive query: Puts burden of name resolution on contacted name server.

####DNS caching
* Once name server learns mapping, it caches mapping.
* Cahce entries will get disappear after a time out TTL
* TLD servers are usually cached in local name servers, thus root name servers are not often visited.

###DNS records
* type=A: value is IP address
* type=NS: value is hostname of autherative name server for this domain
* type=CNAME: value is canonical name
* type=MX: value is name of mail server associated with name

### Attacking DNS
* DDoS attack (distributed denial-of-service): Bombard root server with traffic, Bombard TLD servers (Potentially more dangerous)
* Redirect attacks: Man in the middle attack, DNS poisoning attack (Note: DNS spoofing (or DNS cache poisoning) is a computer hacking attack, whereby data is introduced into a Domain Name System (DNS) resolver's cache, causing the name server to return an incorrect IP address, diverting traffic to the attacker's computer (or any other computer).)
* Exploit DNS for DDoS: Send queries with spoofed source address.

### Definitions
* Peer to peer (P2P)
* RTT (Round trip time) : Time for a small packet to travel from client to server and back.
* FTP: File transfer protocol
