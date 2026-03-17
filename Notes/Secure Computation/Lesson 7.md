(16/03/2026)

#### Malicious verifier:
Verify the graph is 3 color.(Red V)
in the ideal world V don't do no actions.
Mi sono un attimo perso :(



78-73-71-71-65

### Commitment scheme 
commitment scheme but w/o random oracle but with pub key encryption


__to check if something is wrong make a simulation in the ideal world.__

TOOLS: public key encryption (Gen, Enc, Dec) with self verifiable keys
Sender   ----     Receiver
## commitment phase:
send the message encrypted and the pub key (self verifiable)

#### Simulation:
Receiver malicious.
run the protocol internally.
wait for the pair pk and c
send pub key and random cypher text since it cannot distinguish it then it works. It can be replicated in the ideal world.

##### Sender malicious:
send message to the receiver
to do so must run the sender in the ideal world to see if during the process not send the message.

for the commitment part cannot verify that the protocol is secure

to solve this we can ask for also a proof of knowledge other than the claim in the ideal world.
the zero knowledge functionality than can confirm the message is correct

don't send m to the functionality 
take send* i run it then the output is pk,c and the claim that it's the message sent (da rivedere)
the problem with the receiver receiving something in the real world that does not in the ideal is a problem only when the receiver is malicious.


## Opening phase:
sending the secret key is not a possibility does not work since it is not possible to replicate in the ideal world.


Sender has: randomness for the generation of the message, M*(m when s in honest, random string when s is simulated by ideal Rec*)
zero knowledge proof:  receives Pk, c and m and send the receiver 1 saying that the message is verified.
this is by hones tplayers

#### Malicious receiver:
enc a random string  in the sencond phase the withness can't be done bc the message is random.
