## Real World

### Network model

##### Properties

- Fully authenticated network
- Two communication models: 
	1) The Broadcast (or blackboard network): 
			Each party with message m can write it on a public blackboard. Everyone can see what is written on it. All messages are authenticated.
	2) Point to point network
			All parties are connected through a complete  p2p network. Each channel is perfectly authenticated and private.

##### Adversary
- Can corrupt a subset of players: 
		can decide the inputs and randomness of corrupted players and reads their output, that can include the exchanged messages.

- Two standards corruption models:
	1) Hones-but curios corruption:
			The corrupted parties follow the specifications of the protocol. The adversary is passive: he tries to retrieve the private information by observing the transcript (honest at the beginning then act as corrupted)
	2)  Malicious corruption:
			The adversary has fully control over the corrupted parties, and can make them behave arbitrarily in the protocol

- Two standard corruption levels:
	1) Honest majority:
			The adversary can simultaneously corrupt only a strict minority of the player
	2) Dishonest majority:
			The adversary can corrupt all-but-one players



## Ideal World



### Network model

- Parties send their input to a trusted party F through perfectly secure __authenticated channels__

- F computes the output and reveals the result to each party

- The adversary only get some allowed leakage(+ input/output of corrupted parties)


### Simulation
#### Core Idea
Construct a simulator which fools the adversary into believing he is playing the real-world protocol, while making him effectively play the ideal world protocol. Then, we prove that no adversary can [^1]distinguish the simulated protocol from the real protocol.


#### Secure Communication

##### Black board model (public communication)
 - The sender sends his input to F
 - F sends it to the receiver; no leakage
 ![[Pasted image 20260429114949.png]]

__For the real world__

Simulating Alice is easy since Bob generate a  public key honestly.
Simulating Bob is harder, since the other party does not know $\chi_1$

_Solution_
encrypt an arbitrary value instead. The simulation is indistinguishable from the real world
[^1]: in terms of computational indistinguishablility [Computational indistinguishability](obsidian://open?vault=Notes&file=Secure%20Computation%2FArguments%2FComputational%20Inidstinguishability)


