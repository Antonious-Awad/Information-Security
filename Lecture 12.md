# Crypto
- One of the protective methods from attacks & threats
- The process of encrypting a message into an encrypted message at the transmitter & the ability to decrypt the message at the receiver
## Cryptology
The art & science of making & breaking **Secret Codes**
## Cryptography 
Making of the secret code
## Cryptoanalysis
Breaking the secret code
## Crypto
all of the above
# How to speak Crypto
- plaintext: original message
- secret code / secret key / cipher key / cipher code : used to encrypt the plaintext
- ciphertext: result of encryption
## Steps 
- plaintext is encrypted at transmitter using secret key
- cipher key is produced
- cipher key is sent to receiver
- receiver has a secret key which it uses to decrypt the ciphertext into plaintext
## Types of secret key
- Symmetric key cryptosystem
	- same key for encrypting & decrypting
- Public key cryptosystem
	- uses public key for encryption
	- uses private key (each receiver has a different private key) for decryption
---
# Basic assumptions (Kerckhoff's principle)
- the system is completely known to the attacker
- only the key is secret
- crypto algorithms are not secret
## Why do we make such assumptions?
- Secret algorithms should be published to be usable
	-  this will expose the algorithm
- Secret algorithms may become weak when exposed
	- If used based on the fact that the attacker doesn't know the algorithm
- Secret algorithms never remain secret
- better find weakness beforehand
	- don't wait for an attack to discover the weak points

---
- end users do not know much about security
	-  can't make a crypto algorithm or a secret key
- a Third Trusted party is responsible for generating secret keys for the system
	- example
		- bob wants to send a message
		- asks the 3<sub>rd</sub> trusted party for a secret key
		- bob uses the secret key to cipher plaintext
		- ciphertext is then sent
		- 3<sub>rd</sub> trusted party ensures that the cipher text doesn't change during communication from bob to alice
		- alice receives ciphertext
		- alice asks for the secret key for the 3<sub>rd</sub> trusted party
		- alice uses the secret to decipher the text into plain text
- --
# How to cipher text
## Caeser's cipher
- make a table of 2 rows & 26 columns
- 1<sub>st</sub> row: the letters that can be used by bob or alice in writing plaintext
- ![](_resources/Pasted%20image%2020221226212432.png)
- 2<sub>nd</sub> row: Cipher Key
	- Shift the 1<sub>st</sub> row by `n`
	- ex: shift by 3
	- ![](_resources/Pasted%20image%2020221226212559.png)
- change each letter from plain text with its corresponding in ciphertext
- Example
	- Plain text: `four score and seven years ago`
	- cipher text: `IRXUVFRUHDQGVHYHQBHDUVDJR`
- **Same way can be used to DECIPHER text**
- if we have `n` (shift number)
- example:
	- n = 3
	- ![](_resources/Pasted%20image%2020221226212559.png)
	- Ciphertext: `VSRQJHEREVTXDUHSDQWV`
	- Plain text: `spongebobsquarepants`
- `n` is a number between 1 &rarr; 25
- Caeser's cipher is easy to break
- 26 possible keys based  on N

## Simple Substitution
- same as caeser's cipher which shifts by `n` (not necessary)
- after shifting, randomize the order
- ![](_resources/Pasted%20image%2020221226213824.png)
- `26!`or 2<sup>88</sup> possible keys

## Vigenere cipher
- uses polyalphabetic substitution
-  a keywork is used denoting meaning
	- example:
		- keyword CAT = shift by 2 , then shift by 0, then shift by 19
		- 1<sub>st</sub> letter is in a shift by 2 table
		- 2<sub>nd</sub> letter is in a shift by 0 table
		- 3<sub>rd</sub> letter is in a shift by 19 table
		- then repeat
## Double Transposition
- uses matrices
- Key is matrix size and permutations
- ![](_resources/Pasted%20image%2020221226220702.png)
- Key is (3,5,1,4,2) and (1,3,2)
	- number of elements in the first bracket = number of rows
	- number of elements in the second bracket = number of columns
	- do a transposition according to the order inside the brackets
	- ![](_resources/Pasted%20image%2020221226221519.png)
## One-Time pad
- uses logic gates
-  Character code
	- ![](_resources/Pasted%20image%2020221226225859.png)
	- contains the character & its corresponding code
- give a code for each character
- secret code is the same length as the character code
- encryption: Plaintext **⊕** Key = Ciphertext
- Decryption: Ciphertext **⊕** Key = Plaintext
- you will make the secret key (Random generation)
	- **must be the same length of the character code**