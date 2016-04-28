## Network-layer
* Handles datagrams
* Router examines header fields in all IP datagrams passing through it.
* Two key functions:
	* Forwarding: move packets from router's input to appropriate router output.
	* Routing: Determine route taken by packets from source to destination.

## Virtual circuit and datagram networks
* Datagram network provides network-layer connectionless service
* Virtual-circuit network provides network-layer connection service.

## Router
* Two key router functions:
	* run routing algorithm/protocol (RIP, OSPF, BGP)
	* forwaarding datagrams from incoming to oitgoing link

## IP addressing
* IP address: 32 bit identifier for host, router interface.
* Conection between host/router and physical link.
* IP addresses associated with each interface

###Subnets:
* Subnet part: High order bits
* Host part: Low order bits
* Systems in the same subnet can reach each other without intervening router.

###CIDR:
* Classless InterDomain Routing

* To get an IP address:
	* can be hard-coded by system admin
	* DHCP: Dynamic Host Configuration Protocol ("plug and play")

##NAT
* Network address translation
* All datagrams leaving local network have same source NAT IP address.
* So, a local network uses just one IP address as far as the outside world is concerned.

##ICMP
* Internet control message protocol
* Used by hosts and router to communicate network-layer information. eg: error reporting, unreachable host, echo request/reply
* ICMP messages carried in IP datagrams.

##IPv6
* 32 bit address space may soon be completely allocated. This was one of the motivation.
* fixed length 40 byte header.
* No fragmentation allowed.

#### Changes from IPv4
* checksum completely removed.
* ICMPv6: New version of ICMP made.

####Tunneling
* IPv6 datagram carried as a payload in IPv4 datagram among IPv4 routers.
