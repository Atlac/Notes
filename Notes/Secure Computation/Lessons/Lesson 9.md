(25/03/2026)

$\pi_\gamma$ is the prover and verifier and a common input (Zero knowledge proof)
$\pi_\gamma$ =<P(),V()>
P() = r3, x1,r1, r1*, r1^*
V() = r4

commit input = $\gamma$, $F_3$ $\beta$, $c_1$,$c_1^*$

$\gamma$ = $F_3$ ($x_1$)
$\exists$ (x1,r1,r1*,r1*^) = w
c1 = Comm(x1, r1*)
c2 = Comm(r1, r1*^)

will need to convince the verifier about a false claim that with the witness is impossible
this can ba applied to any semi secure protocol


###### From semi-Honest to Malicious:
Too much freedom in choosing the randomness
The strings must not be decided by one player, so to avoid this they must be decided by a coin flip and get the output jointly decided, One get the random bit the other receives nothing
then join with a xor to the string from the other party.


A malicious receiver can compute both keys and knows every message sent 
