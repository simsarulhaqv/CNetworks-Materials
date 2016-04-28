##Transport layer:
* Provides logical communnication between app processes running on different hosts.
* Deal with Segments.
* Multiplexing at sender and Demultiplexing at reciever
* Demultiplexing: Hosts uses IP addresses & port numbers to direct segement to appropriate socket

##Connectionless transport : UDP
* No handshaking between UDP sender and reciever
* UDP uses:
	* streaming multimedia apps
	* DNS
	* SNMP
* No congestion control
* UDP checksum: can detect errors 

## Principles of reliable data transfer
* rdt1.0: reliable transfer over a reliable channel
* rdt2.0: channel with bit errors
	* Checksum is used to detect errors
	* Error recovery using ACK and NAK
	* But what happens if ACk/NAK corrupted?: Retransmits if the ACk/NAK is corrupted. Sender also add a sequence number. Reciver can discard duplicate packets.
	* Stop and wait used: It can wait for recievers response.
* rdt2.1: Handles garbled ACK/NAK. Use sequence number
* rdt2.2: NAK-free protocol: Here instead of NAK, reciever send ACK for the last packet recieved OK.
* rdt3.0: Channel with errors and loss ( So, undelying channel can loss data, ACK etc..). Approach: sender waits reasonable anoutn of time for ACK, retransmits if no ACK recieved.

## Pipelined protocols:
* Sender allows multiple :in-flight" yet to be acknowledged packets
* eg: Go-back-N, Selective repeat.

## TCP
* point to point (One sender, one reciever)
* reliable
* pipelined
* full duplex data (bi directionsal data flow)
* Connection oriented (include handshaking)
* Flow controlled (Sender will not overwhelm reciever)
