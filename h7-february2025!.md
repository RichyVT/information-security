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
$ sudo apt-get install hashcat
          
<img width="860" height="482" alt="image" src="https://github.com/user-attachments/assets/18b29eb0-fac7-4c0b-95ed-7b146142b032" />      
            

-  I then created a new directory called "hashed" for the task using the following commands
$ mkdir hashed        
$ cd hashed          
            
<img width="433" height="59" alt="image" src="https://github.com/user-attachments/assets/33e8a600-d5bf-4874-a1ab-a2c97ec974b5" />      

-  Installed the Rockyou dictionary        
$ wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Leaked-Databases/rockyou.txt.tar.gz            
$ tar xf rockyou.txt.tar.gz        
$ rm rockyou.txt.tar.gz            

<img width="850" height="481" alt="image" src="https://github.com/user-attachments/assets/17843dc3-936f-4e3f-bd2f-cfec6ccf67f9" />      

-  I then installed the 'hashid' tool via pip in order to be able to identify hash ids through the terminal, using the following commands            
$ sudo apt install python3-pip          

<img width="866" height="425" alt="image" src="https://github.com/user-attachments/assets/6f24eafe-dc96-4204-b907-96698c986c44" />

$ sudo apt install hashid          
        
<img width="844" height="426" alt="image" src="https://github.com/user-attachments/assets/8c6a6b03-78af-497c-a0cb-352611dabce5" />
          
-  I then used the hashid to analyze the hash string to identify what type of hash it is, using the example from (https://terokarvinen.com/2022/cracking-passwords-with-hashcat/), '6b1628b016dff46e6fa35684be6acc96'.
-  The hashid tools generates a list of possible hash algorithms that could produce a string with that format but we know from the instructions that the hash is a MD5(Mode 0) hash, which is a common 128-bit hash.          
          
<img width="817" height="382" alt="image" src="https://github.com/user-attachments/assets/00acc3c7-3f17-480a-88a9-13990c311cc4" />
            
-  To crack the hash, I used the following command
$ hashcat -m 0 '6b1628b016dff46e6fa35684be6acc96' rockyou.txt -o solved
            
-  The command means
hashcat - the hash cracking program I installed and will use          
-m 0 - is the type of hash, which can be obtained from the hashid tool, or in this case was given to us                    
'6b1628b016dff46e6fa35684be6acc96' - is the hash I want to crack              
-o solved - save the solution as plain text to a new file "solved" in working directory                
          
<img width="801" height="456" alt="image" src="https://github.com/user-attachments/assets/5e579326-4445-44d3-aff6-0ad4d609fe28" />          

-  and then I used the following command to see what the password is
$ cat solved
          
<img width="415" height="43" alt="image" src="https://github.com/user-attachments/assets/e24df9f8-198e-4c38-8ab0-9fe874cff50f" />       
          
-  the password is 'summer'        
            
-  I then tested another hash '42f749ade7f9e195bf475f37a44cafcb' which is also a MD5 type hash, that I found from (https://www.freecodecamp.org/news/hacking-with-hashcat-a-practical-guide/)            
      
<img width="1012" height="59" alt="image" src="https://github.com/user-attachments/assets/8432a691-58d8-4187-9ac5-c1dab8827642" />

                
<img width="465" height="21" alt="image" src="https://github.com/user-attachments/assets/cd3c6ece-cdfb-4211-bde1-36cd3e696d46" />
      
          
-  The password is 'Password123'      
                








## b) Crack this hash: d595b2086532422bbe654bc07ea030df

-  I ran the hashid tool to see what kind of hash it is

<img width="931" height="386" alt="image" src="https://github.com/user-attachments/assets/79dddc4b-04aa-437a-8767-066a6c4df4e0" />      

-  I assumed it was an MD5 hash, so used the following command to crack it

$ hashcat -m 0 'd595b2086532422bbe654bc07ea030df' rockyou.txt -o solved        
          
<img width="1000" height="46" alt="image" src="https://github.com/user-attachments/assets/3341d2e7-952a-4a17-8034-65d6e449970f" />

<img width="823" height="489" alt="image" src="https://github.com/user-attachments/assets/82458e3d-74c6-4c9d-aecf-6d38f7450ac0" />        

<img width="412" height="21" alt="image" src="https://github.com/user-attachments/assets/f1d4bbc3-0688-4704-aaf7-2654fd618ce6" />

-  The password is 'disobey'



## Sources
https://ia601209.us.archive.org/8/items/Applied_Cryptography_2nd_ed._B._Schneier/Applied_Cryptography_2nd_ed._B._Schneier.pdf
https://terokarvinen.com/2022/cracking-passwords-with-hashcat/
https://hashcat.net/wiki/doku.php?id=example_hashes
