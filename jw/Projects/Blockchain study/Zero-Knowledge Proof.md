---
aliases:
  - zero-knowledge proofs
  - zero-knowledge proof
  - ZK-proof
tags:
  - Blockchain
---

A _zero-knowledge proof_ is a way of proving the validity of a statement without revealing the statement itself. The '__prover__' is the party trying to prove a claim, while the '__verifier__' is responsible for validating the claim.

A zero-knowledge protocol is a method by which one party (the prover) can prove to another party (the verifier) that something is true, without revealing any information apart from the fact that this specific statement is true.

## How do Zero-Knowledge Proof work?
---
A zero-knowledge proof allows you to prove the truth of a statement without sharing the statement's contents or revealing how you discovered the truth. To make this possible, zero-knowledge protocols rely on algorithms that take some data as input and return 'true' or 'false' as output.

A zero-knowledge protocol must satisfy the following criteria:
1. __Completeness__: if the input is valid, the zero-knowledge protocol always returns 'true'. Hence, if the underlying statement is true, and the prover and verifier act honestly, the proof can be accepted.
2. __Soundness__: If the input is valid, it is theoretically impossible to fool the zero-knowledge protocol to return 'true'. Hence, a lying prover cannot trick an honest verifier into believing an invalid statement is valid (except with a tiny margin of probability).
3. __Zero-knowledge__: The verifier learns nothing about a statement beyond its validity or falsity (they have "zero-knowledge" of the statement). This requirement also prevents the verifier from deriving the original input (the statement's contents) from the proof.

### Iterative Zero-Knowledge Proofs

In basic form, a zero-knowledge proof is made up of three elements: __witness__, __challenge__, and __response__.

- __Witness__: With a zero-knowledge proof, the prover wants to prove knowledge of some hidden information. The secret information is the "_witness_" to the proof, and the prover's assumed knowledge of the witness establishes a set of questions that can only be answered by a party with knowledge of the information. Thus, the prover starts the proving process by randomly choosing a question, calculating the answer, and sending it to the verifier.
- __Challenge__: The verifier randomly picks another question from the set and asks the prover to answer it.
- __Response__: The prover accepts the question, calculates the answer, and returns it to the verifier. The prover's response allows the verifier to check if the former really has access to the witness. To ensure the prover isn't guessing blindly and getting the correct answers by chance, To ensure the prover isn't guessing blindly and getting the correct answers by chance, the verifier picks more questions to ask. By repeating this interaction many times, the possibility of the power faking knowledge of the witness drops significantly until the verifier is satisfied.

### Non-Iterative Zero-Knowledge Proofs



## Resources
---
- https://ethereum.org/en/zero-knowledge-proofs/