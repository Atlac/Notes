Exercise from lesson 3 pt.2
![[Pasted image 20260309101531.png]]

DH is done without problem in the ideal and real world for the answer of the query can be simply a message with all 0 encrypted and that makes it computational indistinguishable.

**Hybrid Arguments**: always true for a constant number of experiments. When the number of experiment that could go wrong is 1/2^n, H1 H2... Hi,Hi+1..... Hn for every experiment H the probability of things going wrong doubles (from 1/2^n to 1/2^n-1) to Hn the probability is just 1. So for hybrid arguments the experiments have to be constant. (Poly(n)/2^n is negligible).

The answer of the query the simulation has no idea of how big a* has to be to have a good simulation (needs to be provided) so to the adversary has to know this other than the identity of S. Or the query has a fixed size or it needs to be leaked also.

Functionality don't need _forward secrecy_ (FS) because it's one-shot.  If the next output depends on previous input then we need FS also for the functionality. This is bad in _Adaptive Corruptions_ that the adversary can corrupt not at the beginning but after some times or on the run of an execution.


### Case of active adversary:
MITM: the adversary receives the information and the encrypted message.  In this case can't make a proof since the simulation can't run this case. So or modify the protocol or .. idk. Since the encrypted message can be modified to avoid this go from _CPA_ encryption to _CCA_ encryption.
The adversary is playing as a corrupted client for the server and as a corrupted server to the client. Semi-honest hypothesis prevent random response.

#### Adversary that plays the client and another that interrupt the communication:
The MITM can block the messages. In the real world there is this risk, but not changing any messages. To simulate use the fairness example.

## Fairness
Real world when a two party computation one receives the output before the the other one. **No way to avoid it** for two party computation and all functionality. The one that receives the output first can stop and not make receives the other the result.
Introduce the same type of attack in the ideal world. To do so the Functionality ask to the adversary if to send the output or not, this models the behaviour of the player to stop the computation after obtaining the result.
	F ----> A 
	A----> F  
then F sends or not the results.

For the multy-party case this is not impossible to solve. The others can emulate the player that don't responds. The representation of the other player can avoid this issue by representing the input of the malicious and avoid the problem.


# Commitment Scheme
Sender make an encryption of the message like a safe, the receiver knows that there is a message inside the safe and in the end the sender also sends the key and the receiver can decrypt (open the safe) and obtain the message(ideal world has no cryptography)

	phase 1
sender: message
sends it to a functionality 
the functionality keeps it safe and send the receiver the message was received

	phase 2
sender sends a deliver message 
functionality sends the message to the receiver

There is a random oracle that sends consistent random strings (for the same strings no two random strings can be the response of the same query)

	phase 1
sender: message 
sender send a message to the oracle the message and a salt
then the sender send the answer to the receiver

	pahse 2
sender can send the message and salt to the receiver 
receiver verify with the oracle that the answer is he gets from the oracle using the message and salt to the oracle is the same he received before


Verify:
S is fully malicious: Make a simulation in the ideal world. 
1. Could send a lot of queries to the oracle to search for a collision, if oracle is perfect is ok.
2.  Answer could be trash but there would be no message that correspond to the answer. To simulate this send a random string to the oracle since it will never be received as a message.
So the protocol is also safe against fully malicious adversary, not only the semi-honest.

R is fully malicious:
first activate the real world adversary and see what it does: he wait for a message.
1. feed a random a to the simulation
2. send the real world m to the receiver simulated. If eh ask for the (m,r) to the functionality he will receive a so it's perfect indistinguishability
The real world adversary would be totally fooled by the simulation.

Empirically the oracles can be substituted with  the sha256
Commitment function:
Comm(m): r<-{0,1}
		return sha256(m|r)

__The Simulator was programming the table (the simulator was the oracle)__