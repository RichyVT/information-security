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

#  a) Install OpenSSH server, connect to it using 'ssh' client.        
-  First I updated all operating system and applications using the following command in the terminal:          
$ sudo apt update        
$ sudo apt upgrade -y
<img width="787" height="302" alt="image" src="https://github.com/user-attachments/assets/469086f6-5d87-40a8-bf68-eb4d1161a172" />

-  I then installed OpenSSH server using the following command(which I forgot I already had installed:
$ sudo apt install openssh-server

<img width="797" height="179" alt="image" src="https://github.com/user-attachments/assets/7a0a3f23-5a1f-4aea-8b0a-9e92c935fb93" />          

-  I then checked if whether or not the SSH service was running, it should start automatically after the system boots (and it is installed) using the following command:
$ sudo systemctl status ssh

<img width="837" height="87" alt="image" src="https://github.com/user-attachments/assets/e92f07f6-06a7-43cd-be89-fc848e4429df" />          
                
And we can see it is active and running            
              
-  I then checked to see which port the SSH was listening on by using the following command:
$ sudo ss -tlp
<img width="867" height="96" alt="image" src="https://github.com/user-attachments/assets/a990b190-f6dc-4816-a938-47c521390c31" />
                  
And we can see that it is listening to port 22 (which is the default)
              
-  I then tested if SSH was working locally before trying a remote connection by using the following command:
$ sudo localhost
<img width="792" height="119" alt="image" src="https://github.com/user-attachments/assets/bd2bed48-0033-42c8-9a73-fd0307b032ec" />
              
-   I then found my ip address for the remote connection using the following command:
$ sudo addr show
<img width="886" height="340" alt="image" src="https://github.com/user-attachments/assets/d1ed9f73-81b6-473f-98a4-1dadea1ded2f" />
            
- I then connected to the ip address shown in the previous step using the following command:
$ sudo ssh richard@10.0.2.15
<img width="895" height="361" alt="image" src="https://github.com/user-attachments/assets/85d684d5-c314-4e84-8b01-0ba7cf5bce4d" />          

#  b)Automate SSH connection using public keys.        

-  I generated a SSH keypair using the following command:
$ ssh-keygen -t ed25519 -C "richardalfthan@hotmail.com"

<img width="844" height="402" alt="image" src="https://github.com/user-attachments/assets/0c7ad505-287e-46b2-93ab-0d9b6ef90391" />        
              
-  ed25519 is an algorithm that was used to create the keypair
-  -C adds a comment to identify the key, I used my email account for easy identification
-  The keypair was saved in the default location

-  I then checked to see what my public key was by using the following command:
$ cat ~/.ssh/id_ed25519.pub

<img width="903" height="51" alt="image" src="https://github.com/user-attachments/assets/21490ad3-bc1a-43d4-9419-cd74b49f9632" />                      
              
-  I then copied the public key to the server using the following command:
$ ssh-copy-id richard@10.0.2.15
          
<img width="898" height="243" alt="image" src="https://github.com/user-attachments/assets/8291e07c-196e-469d-bd3e-cd93e140295a" />
                
-  This gave me a prompt to "try to login to the machine using ssh 'richard@10.0.2.15' to make sure that only the key(s) I wanted were added, which I then did
          
<img width="908" height="210" alt="image" src="https://github.com/user-attachments/assets/87f101ee-8e38-477a-ba27-3d34bbb1de8a" />          
                  
#  c) Password manager, open and cloudless. Choose a password manager that 1) works without cloud 2) is free, open source sofware. Install it. Demonstrate its use. Explain why a password manager is needed i.e. what kind of attacks or threats it protects against.

-  For this task I chose KeePassXC
-  To install it, first I did $sudo apt update to make sure everything was up to date

<img width="896" height="132" alt="image" src="https://github.com/user-attachments/assets/376af955-c319-4459-b38d-017aacb8fbb9" />          
                      

-  Then I used the following command to install it:        
$ sudo apt install keepassxc            

<img width="878" height="341" alt="image" src="https://github.com/user-attachments/assets/55936b7c-a4e2-4451-a555-fe297267fa0f" />          

<img width="807" height="631" alt="image" src="https://github.com/user-attachments/assets/38a60646-21ff-4bdb-8f13-572cf3ef070c" />        

-  I created a new database which then gave me some configuration options, what to name it, description, encryption settings.  It will also ask you to create a "Master password" that is needed to access the database, so it is essential that this password is both secure and memorable      
<img width="1471" height="631" alt="image" src="https://github.com/user-attachments/assets/9140d257-dbf0-4950-ba98-6e07a515198a" />

<img width="801" height="553" alt="image" src="https://github.com/user-attachments/assets/efa2c319-bb0f-4eb2-8b6b-9ba525ac17d4" />          

<img width="811" height="632" alt="image" src="https://github.com/user-attachments/assets/6c0a3fdd-5787-4d4f-aeb2-c7f61e1da45a" />
                  
-  Once the database is created and the configuration is complete, you can click on the entry dropdown tab, and click on "Add Entry".  Instead of typing a password, you can click on the dice icon which is KeePassXC's password generator which offers options for length, character types, and will generate a password for you, which is better than having you try to come up with your own          
-  The generated password will be completely random and almost impossible for humans to predict or remember
-  After adding the website URL and username, it is possible to use KeePassXC to login with the password that was added to the database.  Navigatge to the page, return to KeePassXC, select the entry and press CTRL+V and it will automatically switch back to your browser and type your username and password and let you login normally.  This eliminates the need for copying/pasting and makes sure you never manually type your password that could potentially be captured by keyloggers
-  Since it is a cloud-free password manager, its the users responsibility to backup the password database so by saving/copying the .kdbx file to multiple locations in different computers, USB stick, external harddrives it is possible to ensure that there is always a backup available
-  KeePassXC relies on strong cryptography (AES-256 encryption) that makes it hard to crack, e.g. brute-force attacks will be computationally expensive and even if the database is stolen, it is a massive challenge to break the encryption that is protected by the "Master password"
-  This shifts the users security from many weak points to one strong point.  Instead of having multiple websites secure your password, I only have to protect one master password and keep my database file secure
-  The open-source aspect provides extra security through transparency.  Unlike proprietary passowrd managers where you have to believe and trust the companys claims, KeePassXC's code can be reviewed by security professionals which provides valuable feedback and can help identify and fix any potential vulnerabilites
-  Password managers are one of the most impactful security tools available to ordinary users.  By eliminating the need to reuse/recycle passwords and enabling truly random passwords, they provide protection against a lot of credential based attacks while making daily password use easier
-  KeePassXC provides this protection without the need for cloud services or subscription fees, which gives the user almost complete control over their digital and online security

<img width="1483" height="636" alt="image" src="https://github.com/user-attachments/assets/96ff4e83-464a-4bc6-bec4-6399b7287bef" />
            













          
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
                    
-   _O_'_E is probably 'you're' so        
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
https://keepassxc.org/        
https://www.pcworld.com/article/2010172/keepassxc-password-manager-review.html            
https://en.wikipedia.org/wiki/OpenSSH        

