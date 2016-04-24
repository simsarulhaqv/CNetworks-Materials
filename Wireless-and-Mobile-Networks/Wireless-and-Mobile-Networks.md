#Wireless and Mobile Networks

#Introduction

On a higher abstraction we can classify wireless networks according to two criteria,
1) whether a packet in the wireless network crosses exactly one wireless hop or multiple wireless hops
2) whether there is infrastructure such as a base station in the network

* Single-hop, infrastructure-based: examples: 802.11, 3G cellular network.
* Single-hop, infrastructure-less: exmples: Bluetooth networks, 802.11 networks in ad hoc mode.
* Multi-hop, infrastructure-based: examples: wireless mesh networks.
* Multi-hop, infrastructure-less: examples: mobile ad hoc networks (MANETs), vehicular ad hoc network (VANET).

#Wireless

##Wifi: 802.11 Wireless LANs

* Wireless hosts communicate through the base stations.
* Host must associate with an AP

1) 802.11 Passive scanning:
* Beacon frames are sent from the APs.
* Association request frame sent from selected host to AP.
* Association response frame sent from selected AP to host. 

2) 802.11 Active scanning:
* Probe request frame broadcast from a host.
* Probe response sent from APs.
* Association request frame sent from host to selected AP.
* Association response frame sent from selected AP to host.

#### IEEE 802.11 Multiple access

1) MAC protocol: CSMA/CA
* IEEE 802.11 standard for WLAN defines a distributed coordination function (DCF) for sharing access to the medium based on the CSMA/CA Protocol.
* Collision detection is not used here.
* 802.11 Sender.
	* If sense channel idle fir DIFS then transmit entire frame. (No collision detection).
	* If sense channel is busy then start a random backoff time. Transmit again when the timer expires. If no ACK again, increas the ackoff time. Since we choosed a random backoff time initialluy, there is a better chance to avoid collision, even if is same backoff algorithm. Even if we got collision after, to avoid futher collision which may be due to overloaded network can be resolved by increasing backoff time during the futher attempts.
* 802.11 receiver.
	* if frame recieved OK, return ACK afrer SIFS. 

2) Avoiding collisions.
* Allow sender to "reserve" channel rather than random access of data frames.
	* Sender first send small request-to-send (RTS) packets to Base station (BS) using CSMA.
	* BS then broadcasts clear-to-send (CTS) in response to RTS
	* CTS is heard by all nodes. This method recduces the collision problem introduced by the hidden node problem.
* Avoid data frame collisions completely using small reservation packets.

#### Mobility within the same subnet.

* As the host move away from the base station, the BER increases and the SNR decreases. Increased BER is not good for transmission, so when BER becomes too high, switch to a lower transmission rate (With lower SNR), but with lower BER too. 

##Cellular Internet Access

* Two techniques for sharing mobile-to-BS radio spectrum.
	* Combined FDMA/TDMA: Divide spectrum in frequency channels, divide each channel into time slots.

#Mobility

## Principles: addressing and routing to mobile users

## Mobile IP

## Handling mobilty in cellular netorks

## Mobility and higher-layer protocols



##Definitions:
Wireless links: A host connects to a base station or to another wireless host through a wireless communication link.

Base station: A base station is responsible for sending and receiving data to and from a wireless host that is associated with that base station. Cell towers in cellular networks and access points in 802.11 wireless LANs are examples of base stations.

Handoff: When a mobile host moves beyond the range of one base station and into the range of another, it will change its point of attachement into the new base station. This process is called Handoff.

Hop: In computer networking, a hop is one portion of the path between source and destination.	

Ad hoc Networks: In ad hoc networks, wireless hosts have no such infrastructure with which to connect. In this case, the host themselves must provides services such as routing, address assignment, DNS-like name translation, and more.

SNR: Signal-to-Noise ratio usually measured in decibels(dB).

CDMA: Code division multiple access (CDMA) belongs to the family of channel partitioning protocols.

AP: Access point.

Beacon frames: Beacon frames are transmitted periodically to announce the presence of a wireless LAN.

MAC: Media access control. The MAC sublayer acts as an interface between the logical link control (LLC) sublayer and the network's physical layer.

CSMA/CA: Carrier sense multiple access with collision avoidance (CSMA/CA) in computer networking, is a network multiple access method in which carrier sensing is used, but nodes attempt to avoid collisions by transmitting only when the channel is sensed to be "idle".

Hidden node problem: In wireless networking, the hidden node problem or hidden terminal problem occurs when a node is visible from a wireless access point (AP), but not from other nodes communicating with that AP.

BER: Bit error ratio. For better transmission, this should be lower.

SNR: Signal to noise ratio. For better transmission, this should be higher.
