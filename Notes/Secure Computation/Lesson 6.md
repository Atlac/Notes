(11/03/2026)
book: Efficient secure Two-party  Protocols Technoques and Contructions
# Commitment Functionality

![[SecComp2PC.pdf#page=52]]

Zero Knowledge Proof of Knowledge:(ZK PoF)
![[SecComp2PC.pdf#page=53]]

F_ZKPoK is a funtionality s.t. M(x,w) = 1 or 0 iff x belong to L

P(rover): input=(x,w)
sent it to F_ZKPoK
F_ZKPoK will sent it to the V(erifier) x,b,L where b is the result of M(x,w)

Find that a language is NP-complete so that every NP language can be mapped to the NP-complete one and run the protocol for that.

3COL: language that is NP-complete
Consist in all strings that consist in nodes that can be colored using three colors and every node connected by an edge has a different color
![[SecComp2PC.pdf#page=54-56]]
1. random permute the colors
2. pick random edge (two nodes that share the edge)
3. send keys for the endpoints
4. accept if colors are different

What happen if prover  is malicious and the edges are not 3 colors????


	P							V
1. c1...cn (from P to V)
2. e = (i,j) (from V to P)
3. open ci open cj (from P to V)

### Adversary:
##### Malicious Prover: 
Simulate the rw Prover p* to do so the iw P is behind the V
1. c1...cn (from P*)
2. e = (i,j) (from V to P*) 
3. open ci open cj (from P* to V)
But this don't works because the iw P* don't know the w (witness)only the x that is the G (from the real world component) so P* can't give a proof that is 3 color and the protocol is either insecure or i can't prove that is secure
The witness is the coloring of the graph

the iw P* can ask for the other edges to have the colors for all vertices (fixed randomness)
P* since it does not have memory asking multiple times with fixed randomness don't change his view
The verifier can be tricked since the prover can pick a random edge that can happen that P* has picked that two edges that are actually 2 different color
the protocol fail in the real world since it's difficult that the actual node i and j are asked


Soundness= 1/|E| 

Problem is you can redo this protocol over the number of edges and parameters
n*|E| and eventually it will pass the test 
this can also used to pass the test and if the queries are well done you get a lot of witness to verify to make consistency checks

#### Malicious Verifier:
exercise