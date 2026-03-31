(30/03/2026)
__GMW Compiler__
Generally it work badly.
To have security against malicious player there is another compiler.

## MP-SPDZ:
documentation on [github](https://github.com/data61/MP-SPDZ?tab=readme-ov-file) or on [site](https://mp-spdz.readthedocs.io/en/latest/)
![[MP-SPDZ-basic.pdf#page]]
pro: 
- can use multiple algorithms,
- language python like
- use directly to get executable but can also enrich the code of the circuit with python like code 
cons: 
- a bunch

two party computation of set intersection
$P_1$ -($S_1$)->[intersection]<-($S_2$)-$P_2$
then:
$P_1$<-($S_1$ $\cap$ $S_2$)-[intersection]


but it needs to be specified how to compute the intersection
Be S=$\emptyset$ for every element of $S_1$ and for every element of $S_2$ if $e_1==e_2$ add $e_1$ to S

Write the code for the functionality:
File .mpc is the actual code 
(secure integer means that only the player assigning it can see it)
input length don't need to be secure integer since it's known
party_set = Array(n, sint) this define an array of n elements and the elements are secure integers

Exercises:
1) Write the circuit for 2pc aiming at checking some bio-metric correspondence with an error tolerance
2) Write the circuit fora a 2pc of psi that can be used by python programs avoiding the quadratic overhead of the example the previous slide (suggestion: if PRF(k,x)=PRF(k,y) when x=y and PRF(k,z) leaks no information about z if you don't know k, k random string)


Random OT(obliviuos trnafer)
$m_0$ and $m_1$ -> OT<-$c$
			|-->$m_c$

Random OT:
$m_0$,$m_1$ <-OT->$m_c$,$c$
much cheaper and can be precomputed overnight but needs at least to have computed OT one time before

d is c (private of the sender)encrypted with c$ that is like an otp so that no leak is done
![[optimiz (3).pdf#page=14]]


![[optimiz (3).pdf#page=16]]
symmetric encryption and D-H is good if you want to hide information.

![[optimiz (3).pdf#page=20]]

cons: very expensive to run

to avoid the fake garbled circuit we repeat the request, technique called cut-and-choose, so that you can check the garbage and avoid it

what if i get different output from the circuits?(Majority Circuit)
circuit disagree they could be designed so that the if the bit is 1 or 0 it could bring to an abort or not so that the adversary to know if the bit is 1 or 0.


even if the circuit is ok the input may not be ok so this bring to execute malevoilous code