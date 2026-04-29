provide security at network level.
part of ipv6 and addon of ipv4
authentication heather is just providing authenticity and integrity to the packet

Security associantion: need to agree on something to grant security.

Can also be asymmetric  where both have to give and ask for verification
pressure key is for limited number of applications.

Account for 2 different type of modes, Transport mode and Tunnel mode
transport mode protect the payload, Encryption at network level, destination will know how to decrypt
tunnel mode make the whole packet in a new ip packet making the whole packet secure

tunnel mode authenitcate the packet and some headers

in transport mode encrypt the payload and any ipv6 after the ESP header


ESP with IPv4 
ecryot and add esp auth part to authenticate