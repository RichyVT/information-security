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


#  a) Install Hashcat. Test it with a sample hash. See Karvinen 2022: Cracking Passwords with Hashcat

-  First I updated all apps with the $ sudo apt-get update command in the terminal

<img width="816" height="514" alt="image" src="https://github.com/user-attachments/assets/76536ae2-e41a-4780-b0f7-f24698f8346b" />      

-  Then I installed hashcat with the following command
$ sudo apt-get -y install hashid hashcat wget

<img width="772" height="98" alt="image" src="https://github.com/user-attachments/assets/0de71f50-3d77-4561-beed-4b8cc7770d61" />        

-  I then created a new directory called "hashed" for the task using the following commands
$ mkdir hashed
$ cd hashed

<img width="433" height="59" alt="image" src="https://github.com/user-attachments/assets/33e8a600-d5bf-4874-a1ab-a2c97ec974b5" />      

-  Installed the Rockyou dictionary
$ wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Leaked-Databases/rockyou.txt.tar.gz
$ tar xf rockyou.txt.tar.gz
$ rm rockyou.txt.tar.gz

<img width="850" height="481" alt="image" src="https://github.com/user-attachments/assets/17843dc3-936f-4e3f-bd2f-cfec6ccf67f9" />      








b) Crack this hash: d595b2086532422bbe654bc07ea030df





## Sources
https://ia601209.us.archive.org/8/items/Applied_Cryptography_2nd_ed._B._Schneier/Applied_Cryptography_2nd_ed._B._Schneier.pdf
