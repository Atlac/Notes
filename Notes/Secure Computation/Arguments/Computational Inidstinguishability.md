

#### DEFINITION:

Two probability ensembles $\mathcal{X} = \{X_n\}_{n \in \mathbb{N}}$ and $\mathcal{Y} = \{Y_n\}_{n \in \mathbb{N}}$ are computational indistinguishable, denoted $\mathcal{X} \overset{c}{\equiv} \mathcal{Y}$, if for every probabilistic polynomial-time distinguisher  $D$ there exist a negligible function $\mathsf{negl}$ such that $$ \left| \Pr_{x \leftarrow X_n} [D(1^n, x) = 1] - \Pr_{y \leftarrow Y_n} [D(1^n, y) = 1] \right| \leq \mathsf{negl}(n) $$

##### Explanation
It means that even if two distributions or systems are mathematically different, a computationally bounded (polynomial-time) adversary cannot feasibly tell them apart.
In the context of the simulation model for secure computation, this concept is used to prove that a real-world protocol is as secure as an ideal-world scenario. To do this, a simulator is constructed to emulate the honest parties from the real world, while making the adversary effectively play the ideal-world protocol. The simulator's goal is to **fool the adversary into believing they are participating in the real-world protocol**. A protocol achieves security if the **distributions of the adversary's view**, combined with the inputs and outputs of the honest parties, are computationally indistinguishable between the real execution and the simulated one.

A concrete mathematical example of this concept is the **Decisional Diffie-Hellman (DDH) assumption**. The DDH assumption asserts that the following two distributions are computationally indistinguishable (denoted by the ≈ symbol):

1. A valid Diffie-Hellman tuple: $\{(ga,gb,g^{ab})∣(a,b)←Zp2​\}$
2. A completely random tuple: $\{(ga,gb,gc)∣(a,b,c)←Z_p^3​ \}$

Even though the third element in the first tuple is strictly tied to the exponents a and b, while in the second tuple it is a completely independent random exponent c, an adversary does not have the computational power to identify which tuple they have been given

Computational indistinguishability is one of three fundamental indistinguishability concepts used to evaluate security, sitting alongside **statistical** and **perfect** indistinguishability.

