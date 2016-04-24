#Link Layer

#Introduction

### Terminology
* Hosts and routers as nodes
* Communication channels that connect adjacent nodes along communication path as links
* Frame, encapsulates datagram

Date link layer has the responsibility of transfering datagram from one node to physically adjacent node over a link.

### Link layer services:
* Encapsulate datagram into frame, adding header, tailer.
* "MAC" addresses used in frame headers to identify source, dest.
* Ensure reliable delivery between adjacent nodes.
* Seldom used on low bit-error link (Fiber etc). Wireless links have high error rate.
* It maintains the flow control between sending and recievind nodes.
* It helps in error detection.
* Reciever identifies errors and correct it.

###Link Layer
* Link layer is implemented in each and every host.
* Implemented in adapter aka network interface card
* Attaches to hosts system buses.
* Combination of hardware, software and firmware.

####Error Detection
* There is EDC(Error detection and Correction) bit.

####Parity checking
* Single bit parity detects single bit errors.
* Two dimensional bit parity detects and corrects single bit errors.

####Internet checksum
* goal is to detect errors.

####Cyclic redundancy check
* More powerful error detection.
* View data bits D, as binary numbers.
* Choose r+1 bit pattern (generator) G.
* Choose r CRC bits, R, such that <D,R> is dividible by G.
* Reciever knows G, divides <D,R> with G. If non-zero remainder, error detected.
* Can detect all burst errors less than r+1 bits.

###Multiple access protocols
* Here collision can happen if node receives two or more signals at the same time.
* Multiple access protocol is an algorithm that determines how nodes share channel.
* When only one node want to transmit, it can send at rate R.
* When M nodes need to send, each node can send at rate R/M.

###MAC Protocols: Taxonomy
* Three broad classes:
	* Channel partitioning: Allocate channels to smaller pieces and allocate piece to node for exclusve use.
		* TDMA: Access to channels in rounds. Each station geys fixed lenght slots in each round. Unused slots go idle.
		* FDMA: Channel spectrum divided into frequency bands. Each station assigned fixed frequency bands. Unused transmission time in frequency bands fo idle.
	* Random access: Channel not divided, allow collisions. Can recover from collosions.
		* Slotted ALOHA: 
			* All frames have same size. 
			* Time divided into equal size slots (to transmit one frame). 
			* If two or more nodes transmit in a slot, all nodes detect collision.
			* If no collision, node can send a new frame in next slot.	
			* If collision, node retransmits frame in subsequent slot with probability p until success.
			* Collisions will waste the slot.
			* Single active node can transmit data at full rate.
			* Max efficiency = 1/e = 0.37
		* Unslotted ALOHA:
			* No synchronization.
			* When frame first arrived, it is transmitted
			* Collision probability increases.
			* This is pure ALOHA with efficiency = 1/(2e) = 0.18 
		* CSMA (Carrier sense multiple access) [Listen before transmit]
			* If channel sensed idle : transmit entire frame
			* If channel sensed  busy : defer transmission
			* Collision may occur when two nodes not hear each other. Collision makes the entire packet transmission wasted.
			* efficiency = 1/(1+(5tp/tt))
	* "Taking turns": Nodes takes turns to send data. Nodes with more data to send take more longer turns. 
		* Polling:
			* Master initites slaves to transmit in turns.
			* Includes polling overhead and heavy latency.
			* Single point failure of master will make failure.
		* Token passing:
			* Control token passed from one node to next sequentially.


##LAN
###MAC addresses and ARP
* MAC address: Used to get frame from one interface to another physically-connected interface.
* Media access controller (MAC) is a unique identifier assigned to network-interfaces for communication on the physical network segement.
* 48 bit MAC address burned into NIC ROM also sometimes software settable.

###LAN addresses and ARP
* Each adapter on LAN has unique LAN address.

### ARP: Address resolution protocol
* We can find MAC address knowing the IP address using the ARP table.
* Suppose A don't have B's MAC address in ARM table to transmit datagram. So A broadcast ARP query packet containing B's IP address. B recieves A's MAC address and replies to A with its MAC address. A then caches IP-to-MAC pair in its ARP table until TTL (Time to Live).
* ARP is "plug-and-play". Nodes create their ARP table without intervension from the netwrok administartor. 	

### Ethernet
* It is connectionless. No hand shaking between sending and receiving NICs
* Unreliable: Because the receiving NIC doesnt send acks or nacks to sending NIC

### Ethernet switch
* Link layer device.
* Store and forward ethernet frames.
* Transparent: Hosts are unaware of the presence of switches.
* Plug and play: Switches do not need to be configured.

### Switches vs routers
* both are store and forward (Router examine network-layer) (Switches examine link-layer)
* both have forwarding table (Router use IP addresses to compute table using routung algorithms) (Switch compute table using MAC addresses)

###VLAN
* Virtual Local area network.
* Switches supporting VLAN capabilities can be configured to define multiple virtual LANs over single physical LAN infrastructure.

###Link layer virtualization
####Multiprotocol label switching (MPLS)
* Initial goal was to make high speed IP forwarding using fixed length label(instead of IP address).
* MPLS capable routers also known as label-switched router.
* Forward packets to outgoing interfaces based on label value (Without looking into IP address).
* MPLS forwarding decisions can differ from those of IP. (MPLS forwarding table is distinct from IP forwarding tables)
* In IP routing, path to destination is determined bt destination address only. But in MPLS routing path to the destination address is determined by both source and destination address.

###Data center networks
* Challenge is that multiple applications, each serving massive number of clients. Managing, load balancing etc...
* Load balancer: application layer routing. This hide data center internals from client. Load balancer receives external client requests. Direts the workload to the data center and returns the results to the external client.
* There will be rich interconnection among the switches. Hence, increased throughput between racks (Since multiple routing paths available).
  

##Definitions:
* DOCSIS : Data over cable service interface.
* Forwarding table: To find the proper interface to which the input interface should forward a packet.

