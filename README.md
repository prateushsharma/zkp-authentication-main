# ZKP gRPC Client/Server for Authentication

This project implements a gRPC server and client leveraging the Zero-Knowledge Proof (ZKP) Rust library for secure authentication. The integration of ZKP with gRPC ensures that users can be authenticated without revealing sensitive information, enhancing privacy and security. gRPC, a high-performance, universal RPC framework, is employed to handle communication between the client and server.

## Setup

1. **Choose a large random prime number** `q`.

2. **Choose an element** `g`, such that:
   - \( g \) belongs to the cyclic group \( G_q \) and will serve as the generator.
   - **Cyclic Group Definition**: Set of numbers: {1, ..., \( q-1 \)}.
   - A cyclic group consists of numbers whose greatest common divisor (gcd) with \( q \) equals 1.

3. **Choose random integers** `a` and `b`.

4. **Compute the values** `<g, A, B, C>` and send them to both the prover and the verifier:
   - \( A = g^a \mod q \)
   - \( B = g^b \mod q \)
   - \( C = g^{(ab)} \mod q \)

## Proof Generation

In this phase, the prover aims to demonstrate knowledge of the secret `x` to the verifier `n`.

### Steps:

1. **Compute** `Y1` and `Y2`:
   - \( Y1 = g^x \mod q \)
   - \( Y2 = B^x \mod q \)

2. **Choose a random number** `s`, which in this case is **300**.

3. **Calculate**:
   - \( z = (x + a \cdot s) \mod q \)

## Verification

The verifier checks the validity of the proof provided by the prover.

### Steps:

1. Verify that:
   - \( g^z \mod q = A^s * Y1 \mod q \)

2. Verify that:
   - \( B^z \mod q = C^s * Y2 \mod q \)
