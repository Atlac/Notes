one single host that handle request from several users
proxy is natting and firewall allow only between web and proxy
proxy is invisible(not transparent) to the users
more control over the requests
proxy has control over the request 
client needs to talk to the proxy for the request and proxy then will make the real reqeust for the real server and return a document to the client


to make it transparent use a http to make the proxy make a ftp (file transfer protocol) request


AAA authentication authorization auditing
introduce checks above the request also perform blacklisting and whitelisting

Caching, store a document locally to then provide locally that resource instead of requesting it again, but had problem to update the document to solve this was added a header __if_modified_since__ to ask a response only of the document was updated.


for the request use http connect and the final communication is between user and server and the proxy server only forward the requests and not being able to read it, this way we can make a tls handshake w/ breaking the tls security
Not all proxy allow connect or limit it to 443

proxy can still make a virus, malware scan but if it's an execurable can't be blocked before reach the client

### anonymier proxy
hide the computer identifier in the request, also any other host in the conection can't see the destination or the requester, also make more anonymizer proxy to make the original link more difficoult to find, to use one make the request private only for the server, the proxy knows the reality.

### SSL forward proxy
make two connection, one client-proxy and the other proxy-server, needed to make and analysis of what come in the network, this makes a more secure connection allowing deeper inspection but give up some privacy, that's what burp proxy does.


### Reverse proxy for IoT access
////
Application firewall is the most powerful can explore the content before deliveiring, read payload of the request, can contain anything armful(SQL injection, cross site scripting, file inclusion and other type of security issues), solved using a WAF web application firewall, 

### TLS accelleration
remove the tls encryption from the proxy so that the server can act on plaintext making works faster.
### SSL offloading
SSL termination
send data unecrypted to the server 


SSL forwarding
....


### Proxy and HTTPS

ssl bump remove certificate and use the real name
if we don't know how cna the host name can send the tls handshake, then the host name is sent in an http request, the proxy needs to know in advance the certificate to send the client

can't use a certificate for all them, the certificate is in the http but it's encrypted

then?
Use SNI (server name indication), so the add the certificate at the start of the handshake.

this makes a privacy issue. to solve the SNI could be encypted to this makes a ESNI
### Socks proxy 
circuit level gateway
similar to http proxy
the request will be forwarded from the proxy


### transparent proxy
the real request come from the proxy and the client don't know about the proxy

