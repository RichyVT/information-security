# H5 Uryyb, Greg!

#  x) 

## € Schneier 2015: Applied Cryptography: Chapter 1: Foundations            

**Cryptography has four main purposes:**       
              
-  Keeping messages confidential     
-  Authentication, verifying who sent them      
-  Integrity, ensuring they have not been tampered with        
-  Nonrepudiation, preventing senders from denying they sent them       
               
**Cyrptography is like a secure communication system with specific vocabulary**        
-  Plaintext is your original message, ciphertext is the scrambled (enrypted) version of that message that is "protected" during its transmission
-  Encryption/encipher is scrambling the message, decryption/decipher is unscrambling the message
-  Historically, security relied on keeping the algorithm a secret (which led to issues when the algorithms were discovered or when someone left the group)
-  Nowadays cryptography seperates the algorithm (which can be public) from the key which remains a secret
-  Systematic algorithms use the same key for both encryption and decryption (sender and reciever agree on a single key before they can communicate securely)
-  Public-key algorithms or assymetric algorithms use different keys for encryption and decryption (encryption key can be made public, but only a person with the corresponding decryption key/private key can decrypt the message)       

**Cryptanalysis is the science of figuring out the plaintext of a message without access to the key by finding a weakness in the cryptosystem**   
        
An attempted cryptanalysis is called an attack, of which there various
-  Ciphertext-only attack:  They have access to the ciphertext of several messages which have used the same encryption algorithm, and have to recover the plaintext of as many messages as possible to deduce the algorithm used
-  Known-plaintext attack:  They have access to both the ciphertext and plaintext of several messages, and have to deduce the key in order to decrypt any future encrypted messages
-  Chosen-plaintext attack:  They have access to ciphertext and the related plaintext for several messages, and have to find the key by analyzing how specific inputs are encrypted
-  Adaptive-chosen-plaintext attack:  The same as chosen-plaintext attack but they can choose new plaintexts based on the result of previous encryptions, and can find the key more efficiently by adaptively probing the encryption system
-  Chosen-ciphertext attack:  They have the ability to decrypt any ciphertext they choose and see the plaintext like having a decryption machine and can find the secret key by analyzing how specific chosen ciphertexts are encrypted
-  Chosen-key attack:  They have some knowledge about the relationships between different keys rather than the data and can exploit the mathematical relationship between them to break the cipher
-  Rubber-Hose cryptanalysis:  The use of threats, blackmail, bribery or torture to obtain the key
     
If you think that your algorithm is secure because the attacker doesn't know your algorithms inner workings, believe that keeping its inner workings a secret or think that someone won't reverse-engineer it, you are wrong.  The best algorithms are the ones that are made public and are available to be analyzed by the academic community        

Different algorithms offer different degrees of security, if the cost to break it is greater than the value of the encrypted data, if the time required to break it is longer than the duration the data must be kept secret or if the data encrypted with a single key is less than the amount of data needed to break it, the algorithm is "probably" safe
      
-  Substitution ciphers (where each character in the plaintext is substituted for another character in the ciphertext) are vulnerable because they keep the letter frequencies
-  Transposition ciphers (where the plaintext remains the same but the order of characters is shuffled around) are vulnerable because they keep the same letters
-  XOR encryption repeats patterns that can be detected
-  One-time pads (where every possible plaintext is equally likely given any ciphertext) are the better option but has significant practical challenges, require truly random keys as long as the message itself and the keys are never reused, you need lots of truly random key material, perfect synchronization between sender and reciever and secure key distribution, so is best used only for low-volume communications.
          
**Computer algorithms**       
          
-  DES (Data Encryption Standard) uses the same key for encryption and decryption
-  RSA is the most popular public-key algorithm which can be used for encryption and digital signatures
-  SDA (Digital Signature Algorithm) is a public-key algorithm which can only be used for digital signatures
        
## Karvinen 2023: PGP - Send Encrypted and Signed Message - gpg        

-  GNU privacy guard is a popular way to encrypt and sign
-  Guides you through the process of installing gpg encryption tool on Linux using the following command lines     
                  
$ sudo apt-get update 
$ sudo apt-get install gpg micro psmisc

-  It generates a keypair, a private key and a public key          
          
$ gpg --gen-key
              
-  If you want to communicate securely with another person, you have to provide them with your public key and they must also generate their own keypair
-  After verifying the intended targets key (establishing trust) it is possible for both people to communicate securely even when sent over untrusted or hostile network, such as the internet by encrypting the message at the senders end of communication, and then decrypting at the recievers end using the generated keypairs
-  Attackers can't read the encrypted messages, and the messages are signed by the sender to verify and make sure the attackers cannot impersonate your contacts

#  a)
          
#  s) Alternative: Do either d) "Pretty Good indeed" or s) "ETAOIN": ETAOIN. Crack this ciphertext:

    HDMH'B TH. KWU'YI AWR WSSTOTMJJK M OWQINYIMLIY! MB KWU BII, BTGPJI BUNBHTHUHTWA OTPDIYB OMA NI NYWLIA RTHD SYIEUIAOK MAMJKBTB. BII KWU MH DHHP://HIYWLMYCTAIA.OWG        

In the text there seems to be a URL: DHHP://HIYWLMYCTAIA.OWG so:
-  D becomes H
-  H becomes T
-  P remains as P
-  O becomes C
-  W becomes O
-  G becomes M
-  I can assume that HDMH'B is 'THAT'S'
-  D becomes A
        
I then replaced these letters in the ciphertext which became:          
THAT'_ IT. _CO'_E ACT CCCITICA__ A CCSENEALER! A_ _CO _EE, _IT_LE _C__TIT_TIOC CIT_ER_ CAC _E _RO_EC OIT_ _RE_CEAC_ ACA_Y_I_. _EE _CO AT HTTP://TERCLARCARIACOM
              
From this I assumed that:
-  B becomes S
-  Y becomes R
                    
 _O_'_E is probably 'you're' so        
-  K becomes Y
-  U remains as U
-  Y becomes R
-  I becomes E
            
I then replaced these letters in the ciphertext which became:      
THAT'S ET. YCU'RE ACT CFFECEAR_ A CCSESREAER! AS YCU SEE, SET_RE SC_STETSTEC CET_ERS CAC SE SRYCEC OET_ FREYCECA_ ACA_RSES. SEE YCU AT HTTP://TERC_ARCAREACCOM        

From this I assume 
-  ET should be IT
-  YCU should be YOU
-  ACT should be NOW so using this I assume
-  E becomes I
-  C becomes O
-  A becomes N
-  T becomes W

So replacing most of the letters in the ciphertext, I can assume the plaintext message is:        

THAT'S IT. YOU'RE NOW OFFICIALLY A CODEBREAKER! AS YOU SEE, SIMPLE SUBSTITUTION CIPHERS CAN BE BROKEN WITH FREQUENCY ANALYSIS. SEE YOU AT HTTP://TEROLARCADIA.COM

    
## Sources
https://mrajacse.wordpress.com/wp-content/uploads/2012/01/applied-cryptography-2nd-ed-b-schneier.pdf     
https://en.wikipedia.org/wiki/Frequency_analysis          

