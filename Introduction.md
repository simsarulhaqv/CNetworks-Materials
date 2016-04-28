## Introduction

* It is a network of networks.
* Various protocols involved in sending and recieving data through internet.
* Various internet standards exists.

* Host send packets of data.
* Takes the application message, breaks into chunks known as packets, of lenght L bits.
* Trasmits the packet into access network at transmission rate R (Also called capacity or link bandwidth).
* Packet transmission delay = time needed to transmit L-bit packet into the link = L(bits) / R (bits/sec)
* Physical link is what lies between transmitter and receiver.
	* Physical media (Guided) include: coax, fiber.
	* Physical media (Unguided) include radio.
	* Twisted pair (TP)

### Internet as a service:
* Internet is an infrastructure that provides services to the applications.
* Also provides a programmming interface to apps.

### Protocols:
* All communication activities in internet are governed by protocols.
* Protocols define the format, order of message sent and recieved among network enitities, and actions taken on message transmission receipt.

### The network core
* Mesh of interconnected routers.
* Packet switching: It is a method that group all tranmitted data into suitably sized blocks called packets, which are transmitted via medium.
* Packets can be forwarded from one medium to the next, accross links on path from source to destination.
* Takes L/R seconds to transmit (Push out)
* In store and forward method: entire packet must arrive at router before it can be transmitted on next link.
* End end delay = 2L/R (Assuming no propagation delay)
* If arrival rate in bits to links exceeds the trasmission rates,
	* Packets will queue, wait to be transmitted on link.
	* Packets can be dropped if memory fills up.
* Routing determines source-destination route taken by packets.
* Forwarding move packets from routers input to appropriate router output.

### The internet structure:
* End systems connect to internet via access ISPs 
* Access ISPs must be in turn connected, for two host to be connected to each other.
* Packet delay:
	* Nobal delay = Processing delay + queing delay + transmission delay + propagation delay
	* Transmission delay already discussed.
	* Propagation delay = d/s, where d is the length of the physical link, s is the propagation speed in medium (~ 2* 10^8 m/s)
* Traffic intensity = La/R , here a is average packet arrival rate.
	* When avarage queuing delay is very small traffic intensity is nearly zero.
	* When average queing delay is moderate, traffic intensity is higher.
	* When average queing delay is large, traffic intensity tends to infinity.
* Traceroute program provides delay measurement from source to router along end end internet path towards destination.
* Packet loss can happen when arrival rate is much more than the transmission rate. (Usually lost packets are retransmitted)
* Throuput is the rate (bits/time unit) at which biits transferred between sender to receiver.

### Network layers:
* Each network layer implements a service.
* Consist of application, transport, network, link and physical..
* Switch consist of physical layer and link layer.
* Routers consist of physical layer, link layer, and network layer.
* Attacks like packet sniffing should be take care of.
* IP spoofing: send packet with false source address.





## Terminology:
* Network edge: Consist of hosts (clients and servers).
* Network core consist of interconnected routers as well
* DSL: Digital subscriber line.
* FDM (Frequency division muliplexing) (Belongs to circuit switching) allows one user to use a particular partition of the frequency.
* TDM (Time division multiplexing) (Belongs to circuit switching) allows a user to use the whole frequency for a particular unit of time.
* ISP: Internet service providers.
