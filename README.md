# Brutus-with-fastecdsa
Brutus with fastecdsa
Brutus Bitcoin Private Key Brute Forcer with fastecdsa

Brutus with fastecdsais a modified copy of Plutus with fastecdsa from imcmurray

Origin: https://github.com/imcmurray/Plutus-fastecdsa

It is modified to generate random private keys until it fits to the given bitcoin wallet address.

To use it, you have to write the bitcoin address in line 14.

Then start it with

python3 brutus.py

Requirements for python ist fastecdsa
Try for example with with pip install fastecdsa

fastecdsa need GMP install. Example for Centos: yum install gmp-devel
pip3 install -r requirements.txt

Proof Of Concept
Bitcoin private keys allow a person to control the wallet that it correlates to. If the wallet has Bitcoins in it, then the private key will allow the person to spend whatever balance the wallet has.

This program attempts to brute force Bitcoin private keys in an attempt to successfully find a correlating wallet with a positive balance. In the event that a balance is found, the wallet's private key, public key and wallet address are stored in the text file plutus.txt on the user's hard drive.

This program is essentially a brute forcing algorithm. It continuously generates random Bitcoin private keys, converts the private keys into their respective wallet addresses, then checks the balance of the addresses. The ultimate goal is to randomly find a wallet with a balance out of the 2160 possible wallets in existence.

How It Works
Private keys are generated randomly to create a 32 byte hexidecimal string using the cryptographically secure os.urandom() function.

The private keys are converted into their respective public keys using the fastecdsa Python module. Then the public keys are converted into their Bitcoin wallet addresses using the binascii and hashlib standard libraries.

A pre-calculated database of every P2PKH Bitcoin address with a positive balance is included in this project. The generated address is searched within the database, and if it is found that the address has a balance, then the private key, public key and wallet address are saved to the text file plutus.txt on the user's hard drive.

This program also utilizes multiprocessing through the multiprocessing.Process() function in order to make concurrent calculations.

Efficiency
With Fastecdsa the efficieny of this code has increased by an average of 50%, from 0.0032457721 seconds (without Fastecdsa) to 0.0017291287 seconds (with Fastecdsa) for this progam to brute force a single Bitcoin address.

However, through multiprocessing.Process() a concurrent process is created for every CPU your computer has. So this program can brute force addresses at a speed of 0.0017291287 ÷ cpu_count() seconds.

Database FAQ
Visit /database for information

Expected Output
Every time this program checks the balance of a generated address, it will print the result to the user. If an empty wallet was generated, then the wallet address will be printed to the terminal. An example is:

1Kz2CTvjzkZ3p2BQb5x5DX6GEoHX2jFS45

However, if a balance is found, then all necessary information about the wallet will be saved to the text file plutus.txt. An example is:

hex private key: 5A4F3F1CAB44848B2C2C515AE74E9CC487A9982C9DD695810230EA48B1DCEADD
public key: 04393B30BC950F358326062FF28D194A5B28751C1FF2562C02CA4DFB2A864DE63280CC140D0D540EA1A5711D1E519C842684F42445C41CB501B7EA00361699C320
address: 1Kz2CTvjzkZ3p2BQb5x5DX6GEoHX2jFS45



Have fun with it and good luck.

Would be happy for a coffee cup donation.

Donate Bitcoin: 18caPgfTVEGgDMAaiJ6A7U9t9RnH1Yez38
 
Donate Digibyte: DFPm29NrC83LjdCYKwpu4j3zg9tQdPp1ek

Ripple: r3pBG89ZnUeFvPmMSJNVTvUvgXSHFKjyKx

ETH: 0x9aaA45e5d58a1a6fA2e6dbD651E9a08f68C9bc40
