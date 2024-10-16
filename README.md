# ZKP gRPC Client/Server for Authentication

This project implements a gRPC server and client leveraging the Zero-Knowledge Proof (ZKP) Rust library for secure authentication. The integration of ZKP with gRPC ensures that users can be authenticated without revealing sensitive information, enhancing privacy and security. gRPC, a high-performance, universal RPC framework, is employed to handle the communication between the client and server.

# Setup
Choose a large random prime number, q.
Choose an element, g, such that g belongs to the cyclic group Gq and will serve as the generator.
Cyclic Group definition:
Set of numbers: {1, ..., q-1}.
A cyclic group consists of numbers whose greatest common divisor (gcd) with q equals 1.
Choose random integers a and b.
Compute the values <g, A, B, C> and send them to both the prover and the verifier.
A = g^a mod q
B = g^b mod q
C = g^(ab) mod q

# Proof Generation
In this phase, the prover aims to demonstrate knowledge of the secret x to the verifier n.

Step 1: Compute Y1 and Y2.
Y1 = g^x mod q
Y2 = B^x mod q
Choose a random number, s, which in this case is 300.
z = (x + a*s) mod q

# Verification

The verifier checks the validity of the proof provided by the prover.

Verify that g^z mod q = A^s * Y1 mod q.
Verify that B^z mod q = C^s * Y2 mod q.
