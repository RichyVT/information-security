# H6 February2025!

#  x) 

## € Schneier 2015: Applied Cryptography: 2.3 One-Way Functions and 2.4 One-Way Hash Functions.

### One-Way Functions

-  Easy to compute forward (x → f(x)) but extremely hard to reverse (f(x) → x)
-  No mathematical proof they exist, but many functions appear to behave this way
-  Cannot be used directly for encryption since messages couldn't be decrypted
-  Trapdoor one-way functions include a secret key that enables easy reversal for authorized users

### One-Way Hash Functions

-  Takes variable-length input and produces fixed-length output (hash value)
-  Acts as a "fingerprint" for data verification
-  Easy to compute hash from input, but computationally infeasible to find input from hash
-  Collision-resistant: hard to find two different inputs producing the same hash
-  Public process with no secret keys (typically)
-  Single bit change in input changes approximately half the output bits
-  Useful for verifying file integrity and preventing data tampering in financial transactions


#### Message Authentication Codes (MAC)

-  Also called Data Authentication Code (DAC)
-  One-way hash function that includes a secret key
-  Hash value depends on both the input data and the secret key
-  Only someone with the key can verify the hash value
-  Can be created from hash functions, block encryption algorithms, or as dedicated MACs

## Sources
https://ia601209.us.archive.org/8/items/Applied_Cryptography_2nd_ed._B._Schneier/Applied_Cryptography_2nd_ed._B._Schneier.pdf
