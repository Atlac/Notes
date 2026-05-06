__Core concept:__ any polynomial-time computable function can be represented and computed by a polynomial-size boolean circuit.

__Idea:__ encrypting the gates such that they can only be evaluated given appropriate keys, while hiding their exact behavior.

Symmetric encryption properties:
- $KeyGen$ generates key
- $Enc_k(m) -> c$  generates a random encryption of the plain text
- $Dec_k(m)$ returns if $c = Enc_k(m)$
- A decryption of a ciphertext with a wrong key $K'$ returns error

# Garbled Circuit:

1. __Replace Bits with random keys:__ Instead of using standard binary values (0s and 1s) for the inputs and outputs of the logical gates, the protocol represents them using randomly generated encryption keys.

2. __Double Encryption:__ The correct output key for a specific gate is encrypted twice, one with the key representing the first input and again with the key of the second input.

3. __Evaluation:__ For this part is needed the correct pair of input keys. This allow for the parties to learn the outcome of the computation and nothing else

4. __Transmitting keys:__ **Oblivious Transfer** allows the evaluating party to receive exactly the appropriate starting input keys they need for their specific inputs, without revealing their inputs to the sender and without learning the keys for the bits they did not choose.

### More in depth

**1. The Symmetric Encryption Scheme** The chapter defines a symmetric encryption scheme consisting of three standard algorithms: Key Generation (KeyGen), Encryption (Enc), and Decryption (Dec). However, it requires one crucial property for this specific use case: **if a party attempts to decrypt a ciphertext using the wrong key, the decryption algorithm explicitly returns an "error"** rather than just outputting random garbage. This ensures that the evaluating party immediately knows if they have successfully unlocked a gate or not.

**2. Encrypting Logical Gates** The chapter then explains how this encryption is applied to the logical gates (like an AND gate) from the Boolean Circuits (Building Block I):

- **Key Representation:** The true binary inputs and outputs (0s and 1s) are replaced by randomly generated keys. For instance, an input wire x will have two keys: Kx0​ (representing 0) and Kx1​ (representing 1).
- **The "Double Encryption" Technique:** To hide the gate's behavior, the output key is encrypted twice using the corresponding input keys. For example, if an AND gate takes inputs x and y and outputs z, the encrypted value for the scenario where both inputs are 0 would look like this: EncKx0​​(EncKy0​​(Kz0​)).
- **Creating the Garbled Gate:** This double-encryption process is repeated for all four possible input combinations of the logic gate (0,0; 0,1; 1,0; 1,1).

**3. Evaluating the Gate** Finally, the four resulting double-encrypted ciphertexts are **shuffled** so that the order does not reveal anything to the evaluator. When a party evaluates the gate, they will only have two specific input keys. They will try to decrypt all four shuffled ciphertexts. Because of the special property of the encryption scheme, three of the attempts will return an "error", and exactly one will successfully decrypt to reveal the correct output key for the next gate.

# Oblivious Transfer

__Properties:__ 
1. __Correctness:__ The Receiver successfully learns their chosen message $s_b$.
2. __Receiver Privacy:__ The Sender learns absolutely nothing about the Receiver's selection bit $b$.
3. __Sender Privacy:__ The Receiver learns absolutely nothing about the unchosen message.

#### How it works:
1. **Key Generation:** The Receiver generates two public encryption keys (pk0​ and pk1​). However, they only create a valid secret decryption key for the public key that corresponds to their choice (b). The other public key is sampled randomly so that it looks valid, but the Receiver has no way to actually decrypt messages sent to it.
2. **Transmission:** The Receiver sends both public keys to the Sender. Because the randomly sampled key is computationally indistinguishable from the valid one, the Sender cannot figure out which key the Receiver can actually use.
3. **Encryption:** The Sender encrypts s0​ using pk0​, and encrypts s1​ using pk1​. They send both of these ciphertexts back to the Receiver.
4. **Decryption:** The Receiver uses their single secret key to decrypt the ciphertext they requested. The other ciphertext remains completely inaccessible because the Receiver never possessed its corresponding secret key.

This mechanism allows the garbled circuit computation to begin safely, as the evaluating party only obtains the exact keys tied to their true inputs, while the creator of the circuit remains oblivious to what those inputs are.