(25/03/2026)

Ripe NCC
training course for IPv6 
Manage network in Europe
Cover activity parts of the tasks in the slides of NCC

#### Threats:

###### IP Spoofing
To avoid spoofing you need that packet have a source identifier of the network
Or reverse path forwarding to see from where the packet is coming from


##### Cover channel:
Hide the message inside antother message in some way like using Traffic and/or Flow Label
-Traffic class = 0 unless QoS is used
-Flow Label = 0

Fix IPv6 header used for 95% of the traffic while the rest 5% can use a non fixed header
flexibility means complexity so you need software to value this complexity
Full chain of headers must be processed for security

Firewall must work on Extension headers since the headers can be moved and so it's needed to analyze them all

Routing header (type 0):
list of headers and their order but this is a traffic amplification over a remote path
 so it's deprecated
Typical attack:
the source want to send a packet and list the routers you want to cross in the order but the adversary can insert always two router so that the packet get stuck between to routers 
like inserting at the end router b and a (where a is malicious) so that when the packet goes to router b it goes back to a and repeat the process

__remove RH0 from the chain__
since it's deprecated and should not be used anymore


##### fragment headers:

flag = 1 more fragment to come 
flag = 0 last fragment

destination host must reassemble the packet but can't do it alone, this is a big problem due to:
- overlapping fragments: every fragment ha indication on where it must be placed to reconstruct the message
- not sending the last packet: the user may not receive the last packet and wait indefinitelly
- Atomic fragment: packet with a fragment header that is self contained (may be to make the filtering more complex)
__solutions: don't accept these packets__
Router advertisement 


##### Smurf Attack:
(da rivedere)

hop limit 255 if else discard since all source must be inside the network

Secure network discovery(SEND) not widely aviable

NDP threats:
Can send unsollicited NA or ananswered NS
Redirection and DoS attack(Mitm)
![[08-NewIPv6Security-Slides.pdf#page=69]]
