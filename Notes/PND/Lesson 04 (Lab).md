**Wirehsark**
![[04-Traffic_monitoring_lab.pdf#page=29]]

Capture filter syntax:
similar to TCP dump (used to capture traffic)
BPF (bercklesy packet syntax) for both there is a command to see the specific but idk
DHCP packet any other host pretending to be a DHCP port is blocked so that is prevented teh spoofing
**GeoIP** allow to filter packet for region


command for lab1 ex4 
kathara lstart


	**PC1**
	ss -ntl
		port 80 http

	connect labs specify what LAN you want to join to do so launch the command "./connect-lab.sh 127.0.0.1 LanA" in the folder "pnd-labs/lab1"


	the page is on 172.17.0.2 the host is on 172.17.0.1

	run wireshark to capture the exchange of messages

	to retrieve the page use 172.17.0.2/ba.php

	stop capturing then analyse the msgs


	differences:
1. the request differ from basic real to digest real
2. the da.sh gives more information to be combined to have a better authentication method (challenge-response) HASH Function.
3. ba.sh: for the request of the authorization the authorization is sent in clear : Basic YW5nZWxvOmFuZ3Nw
4. da.sh: for the request of the authorization not sent but a digest and the username