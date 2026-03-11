(11/03/2026)
![[05-IPv6_addressing.pdf]]
Awareness problem about IPv6 so nobody use it at least in Italy.
The trend is increasing. In India due to the great request of addresses is very used.
NAT was used to protect the network since every packet pass thru it before the network but the firewall does it better.
###### How an address is represented:
8 group of 16 bits (or hextets) = 128 bits 
Typical IPv6 address: __2001:0DB8:AAAA:1111:0000:0000:0000:0100__
1. every leading 0 can be omitted : __2001:DB8:AAAA:1111:0:0:0:100__
2. all strings of all zeroes can be removed and substituted with (::): __2001:DB8:AAAA:1111::100__


![[05-IPv6_addressing.pdf#page=21]]

(page 21 of pdf) Anycast can be used to give the service to a wide area network, to defend from DOS can use the same address for many location so that the request can be distributed and diluted in many places (black hoax)

## Unicast:
### Global Unicast:
Cast that can be reached globally (public addresses of IPv6)
### Link-Local:
Can only be reached on the same link(only the same ethernet connection)

### Loopback:
### Unspecified:
no specified addresses??
### Uniclocal:
(Private addresses of IPv4) We can route packet but only in our network (In link-local can't be done utside the link).
### Embedded IPv4:
collapse IPv4 into IPv6.


/3 fix the first 3 bits are fixed: in 2000::/3 so in 0010 -- 001 is fixed so it's between 2000 and 3FFF since they all starts with 001.


## Global Unicast:(3-1-4)
Prefix: network address of ipv4(3)
Prefix length: equivalent to subnet mask of IPv4(1)
Interface ID: equivalent to host portion of an IPv4 address(4)
(2^32 all the possible ipv4 addresses while for the subnet in IPv6 we have 2^64)
Possibility of temporary addresses(t+his grant privacy)

## Link-Local:
#### EUI-64 Format (Extended Unique Identifier):
add a FFFE in the middle to reach the bit needed from the mac addresses and flip the seventh bit

or use a random value

When to use ipv6 link-local SLAAC od DHCPv6
when join a network use a link local address and ask to reach the network and a router advertisement that specify how to get an ip address all done using link local multicast router advertiser excahnge happen using link local, self negotiate addresses

###### SLAAC:
ICMPv6 3 uses: neighbor discover protocol (same network host directly connected) 
1. instead of using ARP
2. router solicitation 
3. router advertisement
Neighbor solicitation: ask for who has that address (ARP request is inside the Ethernet Broadcast Ethernet)
instead in IPv6 same structure but instead we use IPv6 over the Ethernet no more broadcast Ethernet but a multicast address 
This allow stateless auto configuration


To give the global unicast address use the same system Manual -- static or IPv6 unnumbered

static :interface id from the network prefix or use the mac addresses of the network interface
IPv6 unnamed 


Dynamic :SLAAC (stateless): more flexible but need more attention
DHCPv6 (stateful also used for IPv4)

RA - router advertisement 

FF02 is a multimast due to the FF 
FF80 is a link-local
given a prefix take the address you want FE80 become the default gateway


RGN is better since it grant Privacy